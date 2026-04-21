# Skill hướng dẫn AI văn viết giống Người, không sử dụng các ký tự AI như — (Em dash)

## Tại sao cần cái skill này?

Nếu bạn đã từng dùng ChatGPT, Claude, Gemini hay bất kỳ con AI nào để viết bài, chắc chắn bạn đã gặp cái ký tự này rất nhiều lần: `—`

Đó là em dash (gạch ngang dài). Trông thì đẹp, chuyên nghiệp đó. Nhưng có một vấn đề lớn:

**Không một người bình thường nào tự gõ ra được ký tự này bằng bàn phím hết.**

Bàn phím thường không có phím em dash. Người Việt mình viết bài, chat, post Facebook, nhắn Zalo, comment trên web... 99,9% dùng dấu gạch ngang thường `-` thôi. Chỉ có AI và mấy ông copy qua Word hoặc Google Docs (do auto-correct tự đổi) mới có em dash trong văn bản.

Kết quả là gì? Content của bạn bị lộ là AI viết ngay từ ký tự đầu tiên. Google detect được. Các công cụ AI detector như GPTZero, Originality.ai, ZeroGPT detect được. Khách hàng đôi khi cũng cảm thấy văn "lợn cợn", "không giống người" mà không biết tại sao.

Ngoài em dash ra thì AI còn hay sinh ra một đống ký tự Unicode lạ khác:

- `…` dấu ba chấm gộp thành 1 ký tự (trong khi người thường gõ 3 dấu chấm riêng `...`)
- `"` `"` `'` `'` dấu nháy cong (smart quotes) thay vì dấu nháy thẳng
- `•` bullet tròn thay vì gạch ngang `-`
- `→` `←` mũi tên Unicode thay vì `->` `<-`
- `×` `÷` ký tự nhân chia toán học thay vì `x` `/`
- Non-breaking space, thin space, zero-width space và cả đống ký tự ẩn khác

Mình đã vật lộn với mấy cái này rất nhiều lần khi làm content cho website. Viết xong phải ngồi Find và Replace thủ công từng ký tự một. Xong Google Docs với Word lại tự đổi ngược lại. Fix đi fix lại không biết bao nhiêu lần.

Cuối cùng mình quyết định giải quyết tận gốc: bắt AI không sinh ra mấy ký tự đó ngay từ đầu, thay vì ngồi clean sau.

Đây là skill mình viết ra sau nhiều lần thử nghiệm và đúc kết. Ngắn gọn, đi thẳng vào trọng tâm, không nói nhiều. Áp dụng xong AI viết ra toàn ASCII thường, văn đọc tự nhiên như người Việt ngồi gõ phím viết tay.

## Cách áp dụng cho mọi loại AI

Skill này là một file text thuần, áp dụng được cho bất kỳ AI nào có phần Custom Instructions hoặc System Prompt.

Các bước:

1. Mở file `SKILL.md` trong repo này và copy toàn bộ nội dung
2. Paste vào phần Custom Instructions của AI bạn đang dùng
3. Lưu lại là xong

Vị trí paste trên từng AI:

- **ChatGPT:** Settings > Personalization > Custom Instructions
- **Gemini:** Gems > Custom Instructions (hoặc System Instructions khi tạo Gem)
- **Grok:** Customize > Personality
- **DeepSeek, Qwen, Kimi, các AI khác:** tìm phần Custom Instructions hoặc System Prompt tương tự

Sau khi paste xong, mỗi lần chat AI sẽ tự động áp dụng rule, không sinh ra em dash hay ký tự Unicode lạ nữa.

## Cách áp dụng cho Claude (nhanh nhất)

Claude có khả năng fetch link GitHub và đọc file trực tiếp nên cài rất nhanh. Chỉ cần paste link repo này vào chat và bảo Claude nạp skill là xong.

Ví dụ paste câu này vào Claude:

```
Nạp skill này cho tôi: https://github.com/[username]/[repo-name]
Đọc file SKILL.md và áp dụng vào mọi nội dung viết sau này.
```

Claude sẽ tự động fetch repo, đọc file SKILL.md, và bắt đầu áp dụng rule từ câu trả lời tiếp theo.

### Áp dụng cho Claude Web (claude.ai)

Có 2 cách:

1. **Paste link mỗi lần chat mới** (như hướng dẫn ở trên)
2. **Cài cố định vào Project:** Tạo một Project mới trong Claude, vào phần Project Instructions, paste toàn bộ nội dung file SKILL.md vào. Từ giờ mọi chat trong Project đó đều tự áp dụng.

### Áp dụng cho Claude Desktop / Claude Code / Cowork

Clone repo về máy và copy vào folder skills cá nhân của Claude:

```bash
git clone https://github.com/[username]/[repo-name].git ~/.claude/skills/human-writing
```

Restart lại Claude Desktop hoặc Claude Code. Skill sẽ tự động được nạp và kích hoạt khi bạn yêu cầu viết content.

## Kiểm tra skill có hoạt động không

Sau khi cài, yêu cầu AI viết 1 đoạn văn bất kỳ có chứa suy nghĩ hoặc giải thích dài. Copy đoạn đó vào VS Code, Sublime Text, hoặc bất kỳ editor nào.

Dùng Find (Ctrl+F hoặc Cmd+F) search lần lượt các ký tự:

```
—
…
"
"
'
'
•
```

Nếu tất cả đều hiện "0 results" nghĩa là skill đang chạy đúng. Nếu vẫn còn ký tự lạ, nhắc AI lại 1 lần nữa hoặc kiểm tra xem đã paste đúng phần Custom Instructions chưa.

## Đóng góp

Phát hiện thêm ký tự AI nào hay lộ mà skill chưa cover? Mở Issue hoặc Pull Request, mình sẽ review và merge nhanh.

## License

MIT. Dùng thoải mái cho cá nhân và thương mại.

Tác Giả Thanh Nguyen
https://www.facebook.com/ThanhNDVN/
https://www.tnd.vn/
