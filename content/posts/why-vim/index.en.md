---
title: "Vim"
date: 2023-07-1
lastmod: 2023-10-11
draft: false
description: "Không phải nước tẩy"
summary: "Không phải nước tẩy"
featuredImage: "vim-dam-dac.jpg"
---

Nếu được hỏi một trong những kĩ năng quan trọng nhất mà mình học được qua 4 năm Đại học thì mình sẽ nhanh chóng trả lời rằng đó là Vim.

# Vậy Vim là gì?

Đối với mình, Vim không phải là một phần mềm, nó là một phong cách thao tác với văn bản mà không cần phải dùng phím mũi tên và hạn chế tối đa việc sử dụng chuột:

Note: Mình dùng chữ “thao tác” chứ không phải là “gõ” nhé. Lí do là vì khi xài Vim thì ngoài tính năng gõ bình thường (insert mode) thì chúng ta có thể xóa, copy, paste,… và rất nhiều thao tác khác nhé nhờ vào sự kết hợp giữa Insert + Normal + Visual mode.

Theo wiki: “**Vim** ([/vɪm/](https://en.wikipedia.org/wiki/Help:IPA/English);[[6]](https://vi.wikipedia.org/wiki/Vim_(tr%C3%ACnh_so%E1%BA%A1n_th%E1%BA%A3o)#cite_note-pronounc-6) viết tắt của **Vi IMproved**) là một [trình soạn thảo văn bản](https://vi.wikipedia.org/wiki/Tr%C3%ACnh_so%E1%BA%A1n_th%E1%BA%A3o_v%C4%83n_b%E1%BA%A3n) [miễn phí](https://vi.wikipedia.org/wiki/Ph%E1%BA%A7n_m%E1%BB%81m_mi%E1%BB%85n_ph%C3%AD) và [mã nguồn mở](https://vi.wikipedia.org/wiki/M%C3%A3_ngu%E1%BB%93n_m%E1%BB%9F).”. Với cách hiểu này thì Vim là một phần mềm mà bạn sẽ download về rồi gõ văn bản trên đó. Khi gõ chữ trên phần mềm Vim, chúng ta sẽ có thể sử dụng bàn phím ở 3 chế độ:

- Insert mode: Gõ chữ bình thường như mọi ngày (a → z, 0 → 9, mũi tên, chuột,…), tương tự như khi dùng Word hay Notepad
- Normal mode + Visual mode: Cho phép các thao tác như delete, copy, paste, undo, search, replace,…

# Tại sao mình lại tìm tới vim?

Lúc đại dịch Covid diễn ra, mình gần như ăn ngủ với chiếc laptop, bàn phím và chuột. Từ học online cho tới chạy đồ án, lúc nào mình cũng phải sử dụng 3 món đó. Tới mức là có lúc cổ tay của mình rất đau và có hôm mình không thể gõ phím được nữa.

Nguyên nhân là do trong lúc làm việc, mình phải di chuyển tay quá nhiều, nhất là tay phải. Trong lúc gõ, mình tay phải của mình rất thường xuyên với sang bên để tìm tới nút mũi tên hoặc chuột. Không những mệt mà còn chậm nữa.

Và thế là mình tìm đến Vim như một liều thuốc để xoa dịu nỗi đau.

Giờ đây thì mình ít khi phải sử dụng chuột và nút mũi tên nữa, chính vì vậy mà tốc độ gõ phím của mình đã nhanh hơn rất nhiều.

Giờ tới lượt của bạn, hãy nhớ lại xem bạn dùng phím mũi tên bao nhiêu lẫn mỗi ngày trong lúc code, hay đơn giản là gõ văn bản:

- Bạn có thấy mệt mỏi khi phải với lấy chuột mỗi khi muốn di chuyển tới vị trí nào đó trên màn hình?
- Bạn muốn gõ phím nhanh hơn?

Nếu câu trả lời là có thì hãy làm bạn với Vim.

Thử làm một phép tính nhỏ:

Giả sử vim giúp bạn tăng hiệu suất lên 5% (đối với mình thì lớn hơn rất nhiều) thôi thì qua mỗi ngày. Và giả sử hiệu suất này sẽ ngày càng giúp bạn làm việc hiệu quả hơn.

Thì sau một năm liên tục sử dụng vim trong công việc, hiệu suất của bạn sẽ tăng lên …

“Nhưng giao diện Vim editor nhìn buồn tẻ quá, không lẽ mình phải xài nó thay vì Word hay VScode hả?”

… giao diện Vim

Thật ra, mình cũng thấy vậy.

# Làm thế nào để bắt đầu học Vim?

Cách dùng vim thì mình sẽ không nói chi tiết bởi mình tin là trên mạng đã có rất nhiều bài hướng dẫn rồi. Mình sẽ để link ở bên dưới.

Học giống như học tiếng Anh vậy á.

Bên cạnh Vim editor huyền thoại đã hơn 31 tuổi, hiện tại có rất nhiều plugin, extension trên Chrome, VScode, hay thậm chí là Windows 10 cho phép bạn thao tác theo phong cách Vim. 

Bởi vậy, một khi thông thạo 3 modes là có thể thi triển kĩ năng cào phím ở hầu hết bất kì nơi nào.

- VScode: [Vim - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim#review-details)
- Pycharm/Intellij: [IdeaVim: Intelligent Vim engine for JetBrains IDEs](https://lp.jetbrains.com/ideavim/)
- Chrome extension: [Vimium](https://chrome.google.com/webstore/detail/vimium/dbepggeogbaibhgnhhndojpepiihcmeb?authuser=1&msclkid=d42842a40a1a1acf7d0820372ee54eeb&utm_source=bing&utm_medium=cpc&utm_campaign=Fill_Chrome%20Extension_Vietnam&utm_term=extensions%20chrome&utm_content=Fill%20PDF). Extension này giúp chúng ta thao tác trên trình duyệt mà không cần phải sử dụng chuột hoặc phím mũi tên
- Windows: [vim-everywhere](https://github.com/lubokkanev/vim-everywhere). Đây là một ứng dụng nhỏ được viết bằng ngôn ngữ AHK. Nó sẽ cung cấp cho chúng ta normal mode + visual mode ở bất kì đâu trên Windows. Dù là trên trình duyệt, notepad, Notion, Evernote,… bất kì đâu mà các bạn có thể dùng nút mũi tên để thao tác.

Một số tips nhỏ:

- Khi mới bắt đầu, mỗi ngày chỉ cần dành ra 10 - 15p để học vim thôi là đủ rồi.
- Thường xuyên luyện vim trong vòng sau vài giờ. để luyện trí nhớ cơ bắp

Mình vẫn dùng Vim đều đặn mỗi ngày, trong từng câu chữ này. 

Và mình vẫn sẽ dùng vim trong tương lai.

> Cảm ơn mọi người đã đọc 🙏
>
> Chúc mọi người một ngày tốt lành🤗
