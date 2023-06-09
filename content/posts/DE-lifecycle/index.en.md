---
title: "Data Engineering Lifecycle"
date: 2023-06-09
lastmod: 2023-06-09
draft: false
description: "Một cái nhìn toàn diện về dữ liệu"
summary: "Một cái nhìn toàn diện về dữ liệu"
featuredImage: "five-stages.png"
---

# Giới thiệu

Trong bài viết này, mình tổng hợp những khái niệm cơ bản về các giai đoạn trong Data Engineering Lifecycle sau khi đọc xong cuốn [Fundementals of Data Engineering](https://www.amazon.com/Fundamentals-Data-Engineering-Robust-Systems/dp/1098108302). Từ đó mình có thể tra cứu thêm về một số khái niệm khi cần thiết.

Mình rất ủng hộ các bạn đọc cuốn này nha.

Theo Sandro Mancuso, có 4 loại sách kĩ thuật (technical books) mà chúng ta cần quan tâm trong sự nghiệp

1. Technology-specific books: Sách thiên về một công nghệ nào đó. Chúng rất có ích nhưng vòng đời ngắn. Nội dung có thể nhanh chóng bị lỗi thời nếu không được cập nhật thường xuyên.
    - [Kafka](https://www.amazon.com/Kafka-Definitive-Real-Time-Stream-Processing/dp/1491936169/ref=sr_1_2?crid=2S21CLBAKWC6&keywords=kafka+data&qid=1686297000&s=books&sprefix=kafka+d%2Cstripbooks-intl-ship%2C464&sr=1-2), [Hadoop](https://www.amazon.com/Hadoop-Definitive-Storage-Analysis-Internet/dp/1491901632/ref=sr_1_1?crid=22W5GO4P9OVRG&keywords=hadoop&qid=1686296934&s=books&sprefix=hado%2Cstripbooks-intl-ship%2C332&sr=1-1),…
2. Conceptual books: Sách thiên về khái niệm. Trong đó có thể rất ích code nhưng nó chứa những kiến thức nền tảng để thẳng tiến trong sự nghiệp (Ví dụ: SE books)
    - [Software Engineering](https://www.amazon.com/Software-Engineering-10th-Ian-Sommerville/dp/0133943038#customerReviews), [Fundamentals of Data Engineering](https://www.amazon.com/Fundamentals-Data-Engineering-Robust-Systems/dp/1098108302) (cuốn sách mình giới thiệu ✅),…
3. Behavioral books: Sách giúp chúng ta quản lí bản thân và làm việc nhóm hiệu quả hơn
    - [The power of habits](https://www.amazon.com/Power-Habit-What-Life-Business/dp/081298160X), [Deep Work](https://www.amazon.com/Deep-Work-Focused-Success-Distracted/dp/1455586692),…
4. Revolutionary books: Những cuốn sách “kinh điển” làm thay đổi cách làm việc của chúng ta. Ví dụ (Agile books)
    - [Agile](https://www.amazon.com/Essential-Scrum-Practical-Addison-Wesley-Signature/dp/0137043295/ref=zg_bs_379406011_sccl_1/144-2182307-6358927?psc=1), [Clean code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882),…

Cuốn sách này đã giúp mình hiểu rõ hơn rất nhiều khái niệm trong Data Engineering và có thể liên kết chúng lại với nhau.

Trước đây, mình rất hay bị cuốn vào những phần chi tiết và quên đi bức tranh tổng thể của vấn đề. Ví dụ khi tìm hiểu về MySQL thì mình có cắm đầu cả ngày để nghiên cứu sự khác biệt giữa các SQL engines.

Do vậy việc duy trì một bức tranh tổng thể về vòng đời của dữ liệu sẽ giúp mình tránh bị lạc lối trong quá trình tìm hiểu. Đối với mình Data Engineering Lifecycle đã giúp mình hệ thống lại những kiến thức, kĩ năng liên quan tới DE mà mình đã được học từ trước, trả lời những câu hỏi như:

- Tại sao không phân tích ngay trên OLTP system thay vì trên DW/DL/LH?
- Hadoop, Spark, Kafka được dùng để làm gì?
- Dữ liệu được sử dụng để làm gì? Phân tích? Build ML models? Và gì nữa?

{{< image src="./five-stages.png" caption="Data Engineering Lifecycle. [Source](https://www.amazon.com/Fundamentals-Data-Engineering-Robust-Systems/dp/1098108302)" src_s="" >}}

Data Engineering Lifecycle cho chúng ta cái nhìn toàn diện về dữ liệu. Trong đó có 5 giai đoạn:

1. `Generation`: Tổng hợp dữ liệu từ nguồn nào?
2. `Storage`: Lưu dữ liệu ra sao?
3. `Ingestion`: Load dữ liệu từ nguồn → đích theo cách nào?
4. `Transformation`: Dữ liệu sẽ được mô hình hóa và biến đổi ra sao?
5. `Serving`: Mục đích sử dụng dữ liệu là gì?

Và mình tin là 4 giai đoạn đầu tồn tại chỉ để phục vụ cho giai đoạn cuối cùng đó là `Serving`.

Thế nên những câu hỏi liên quan tới 4 giai đoạn đầu chỉ được giải đáp khi chúng ta có mục tiêu sử dụng dữ liệu rõ ràng. Nói cách khác, phải trả lời được câu hỏi:

> Chúng ta đang sử dụng dữ liệu để giải quyết vấn đề gì?
> 

# Generation: Nguồn

Khi biết về hệ thống dữ liệu nguồn (Nằm ở đâu? Đặc trưng? Cách dữ liệu được tạo ra), chúng ta sẽ hiểu hơn về đặc trưng của dữ liệu để lựa chọn kho lưu trữ và cách ingest dữ liệu hợp lí.

Hiểu hơn về:

- Nó nằm ở đâu?
- Cách nó được tạo ra
- Đặc trưng của nó

## OLTP systems: Relational + Non-relational (NoSQL)

- OLTP systems lưu trữ trạng thái hiện tại của ứng dụng dưới dạng các tables.
- Row-oriented: Lưu dữ liệu theo dòng → Xử lí lượng lớn thao tác insert/update/delete nhanh chóng tại cùng một thời điểm (Low latency, high concurrency)

## OLAP sytems: Data Warehouse, Data Lake,…

- Data không chỉ xuất phát từ OLTP → OLAP mà còn đi từ OLAP → Analytics/ML
- Column-oriented: Lưu dữ liệu theo từng cột → Hiệu quả cho việc phân tích: đọc và tổng hợp (`sum`, `count`,  `distinct`, …) dữ liệu ở một vài cột quan trọng (sales, salary, price, …)


{{< image src="./row-vs-columnar.png" caption="[Microsoft PowerPoint - Column-Oriented Database Systems FINAL (umd.edu)](http://www.cs.umd.edu/~abadi/talks/Column_Store_Tutorial_VLDB09.pdf) ">}}


| Thao tác | Row-oriented                                                      | Column-oriented                     |
| --- |-------------------------------------------------------------------|-------------------------------------|
| insert 1 record có n thuộc tính (cột) | Viết record vô 1 file                                             | Viết record vô n file               |
| delete 1 record | Xóa record đó ở 1 file                                            | Xóa record đó ở n file              |
| select first_name from table_A | Đọc giá trị salary của tất cả record trong tất cả các files       | Đọc giá trị ở file lưu salary       |
| select sum(salary) from table_A | Đọc giá trị salary của tất cả record trong tất cả các files → Sum | Đọc giá trị ở file lưu salary → Sum |

Tham khảo:

[Column vs Row Oriented Databases Explained - YouTube](https://www.youtube.com/watch?v=Vw1fCeD06YI)

## Khác

- Messages and streams: IoT devices, clickstreams, social media streams,…
- Logs: Database Logs, OS, Applications, Weblogs, Servers, Containers, Networks,…

# Storage: Điểm đến

Trước khi dữ liệu được xử lí để mang lại giá trị thì cần phải có một nơi tổng hợp dữ liệu từ nhiều nguồn khác nhau. Và dưới đây là những nơi phổ biến mà dữ liệu sẽ được load vào:

| Loại | Data Warehouse | Data Lake | Lakehouse |
| --- | --- | --- | --- |
| Kiểu dữ liệu | Structured | Semi-structured, unstructured | Cả hai |
| Tình trạng dữ liệu | Đã được xử lí | Thô | Cả hai |
| Thời gian ingest dữ liệu | Chậm (Do phải build ETL pipelines) | Nhanh (Phù hợp cho ELT pipelines: Load vô DL rồi mới biến đổi sau) | Tùy (Hỗ trợ ETL + ELT pipelines) |
| Mục đích sử dụng | BI | Machine Learning | Cả hai |
| Chi phí | Cao | Thấp | Thấp |

Đọc thêm:

[Data Warehouse vs. Data Lake vs. Data Lakehouse: Which Is Better for Your Business? (simform.com)](https://www.simform.com/blog/data-warehouse-vs-data-lake-vs-data-lakehouse/)

[Data Warehouse vs Data Lake | ETL vs ELT | (ssp.sh)](https://www.ssp.sh/blog/data-warehouse-vs-data-lake-etl-vs-elt/#comments)

[Data Warehouse vs Data Lake vs Data Lakehouse | by Luís Oliveira | Level Up Coding (gitconnected.com)](https://levelup.gitconnected.com/data-warehouse-vs-data-lake-vs-data-lakehouse-d60d586951b1)

# Ingestion: Quá trình di chuyển

Tùy vào mục đích sử dụng, dữ liệu sẽ được di chuyển từ nguồn → đích theo 1 trong 2 kiểu (Batch/Streaming) và bằng nhiều cách khác nhau. 1 quy tắc đơn giản để lựa chọn Batch/Streaming là:

> Chỉ chọn Streaming khi lợi ích mà nó mang lại nhiều hơn chi phí bỏ ra để xây dựng hệ thống Streaming đó.
> 

Dưới đây là một số cách phổ biến để di chuyển dữ liệu:

- Direct Database Connection
- Databases and File Export
- APIs
    - REST, GraphQL, Webhooks, RPC and gRPC
- Change Data Capture
- Managed Data Connectors
- Message Queues and Event-Streaming Platforms
- Web Interface
- Web Scraping
- Moving Data with Object Storage
- Transfer Appliances for Data Migration

Các bạn có thể tham khảo thêm trong sách nhé!

# Transformation/Serving: Biến đổi → Giá trị

Sau khi đã biết về nơi xuất phát, đích đến, cách dữ liệu di chuyển thì giờ tụi mình sẽ quan tâm tới quá trình biến đổi dữ liệu để mang lại giá trị cho doanh nghiệp. Trước tiên, chúng ta phải

## Mô hình hóa dữ liệu

Câu hỏi đặt ra là:

- Mô hình hóa dữ liệu là gì?
- Tại sao lại phải mô hình hóa dữ liệu?

### Mô hình hóa dữ liệu là gì?

{{< image src="./data-modeling.png" caption="[Data Modeling – The Unsung Hero of Data Engineering: Modeling Approaches and Techniques (Part 2) | Airbyte](https://airbyte.com/blog/data-modeling-unsung-hero-data-engineering-approaches-and-techniques#data-vault-modeling-a-flexible-and-dynamic-approach)">}}


Data modeling được đề cập ở đây khác với data modeling trong System Design, khi mà các dữ liệu trong source system được mô hình hóa để x ây dựng bức tranh tổng thể (**Conceptual, Logical, Physical Data Models)** cho toàn bộ dữ liệu của doanh nghiệp để dễ dàng quản lí và tận dụng chúng.

Data modeling trong Data Warehouse/Data Lake được dùng để tổ chức, sắp xếp dữ liệu sao cho DE để quản lí và DA/DS dễ sử dụng nhất.

### Tại sao lại phải mô hình hóa dữ liệu?

Chắc chắn là data modeling phải đem lại lợi ích quan trọng nào đó nên nó mới xuất hiện, phát triển và vẫn còn phổ biến cho tới hiện nay (Ví dụ: kĩ thuật [Dimensional Modeling](https://www.amazon.com/Data-Warehouse-Toolkit-Definitive-Dimensional/dp/1118530802) được giới thiệu vào năm 1996)

Với kiến thức ít ỏi và kinh nghiệm bằng 0 khi viết bài thì mình chưa thể hệ thống rõ ràng về những lợi ích của việc mô hình hóa dữ liệu. Mình đã đọc rất nhiều bài viết nhưng mình vẫn chưa tự thuyết phục bản thân rằng đó thực sự là những lợi ích của data modelling.

Có thể mình sẽ viết 1 bài giải thích chi tiết về lợi ích của data modeling trong tương lai.

### Các kĩ thuật mô hình hóa dữ liệu

- [Inmon](https://www.amazon.com/Building-Data-Warehouse-W-Inmon/dp/0764599445)
- [Kimball](https://www.amazon.com/Data-Warehouse-Toolkit-Definitive-Dimensional/dp/1118530802)
- [Data vault](https://www.data-vault.co.uk/what-is-data-vault/)
- Wide denormalized tables

## Biến đổi dữ liệu

Ở giai đoạn này, dữ liệu sẽ được biến đổi để chuẩn bị phục vụ cho mục đích Analytics hoặc ML

Một số thao tác biến đổi dữ liệu phổ biến:

- Kết hợp từ nhiều nguồn khác nhau
    - `join()`, `union()`, `concat()`,…
- Làm sạch dữ liệu
    - Xử lí missing: `na.drop()`, `na.fill()`, `na.replace()`
    - Xử lí trùng: `dropDuplicates()`
    - Biến đổi string:`trim()`, `lower()`, `upper()`, `regexp_replace()`, `substring()`
    - Regular Expressions: `regexp_extract()`, `regexp_replace()`, or `rlike()` (Ví dụ trích `100000` từ `100,000 VNĐ`)
    - User-Defined Functions (UDFs)
- Tổng hợp dữ liệu: `count()`, `distinct()`, `sum()`, `groupBy()`,..

## Sử dụng dữ liệu

Sau khi dữ liệu đã được biến đổi rồi thì phải sử dụng nó thôi. 

- Analytics:
    - Business Analytics: Sử dụng dữ liệu của quá khứ và hiện tại để build:
        - Dashboards: Cung cấp bức tranh tổng quan về một khía cạnh hoặc toàn bộ khía cạnh của doanh nghiệp (doanh thu, nhân sự,…)
        - Reports: Cung cấp insight cho một vấn đề cụ thể nào đó (report số liệu liên quan tới doanh thu tháng này từ A-Z)
    - Operational Analytics: Phân tích dữ liệu hiện tại để dưa ra những quyết định quản lí hệ thống
    - Embedded Analytics: Ngoài những vấn đề vĩ mô ở tầm doanh nghiệp (Business) thì dashboards, reports có thể được sử dụng trong các ứng dụng nhỏ. (report nhiệt độ của máy lạnh trong ngày)
- ML applications: Sử dụng cho các mô hình Machine Learning/Deep Learning (huấn luyện và dự đoán)

# Cách mình vận dụng Data Engineering Lifecycle

- Khi mới join vô project, mình sẽ hỏi:
    - Dữ liệu được lấy từ những nguồn nào (Generation)
    - Lưu ở DW/DL hay LH? Tại sao? (Storage)
    - Cách di chuyển dữ liệu: Batch hay Stream? (Ingestion)
    - Áp dụng kĩ thuật mô hình hóa nào (Transformation)
    - Phục vụ Analytics hay ML? (Serving)
- Khi thấy 1 tools, product nào thì thì mình đã đặt câu hỏi: Tool đó hỗ trợ cho giai đoạn nào trong Data Engineering Lifecycle?

# Tổng kết

Bài viết này giới thiệu về Data Engineering Lifecycle và những khái niệm cơ bản trong từng giai đoạn Data Engineering Lifecycle. Đây là bức tranh tổng thể về dữ liệu và là xương sống cho toàn bộ những kiến thức DE mà mình đã, đang và sẽ học trong thời gian tới.
