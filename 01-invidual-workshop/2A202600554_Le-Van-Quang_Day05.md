

## App chọn: MoMo — Moni

## 1. Sản phẩm được chọn
**Sản phẩm:** MoMo — Moni
**AI feature:** Trợ thủ tài chính AI / quản lý chi tiêu cá nhân
**Cách truy cập:** App MoMo

**Feature teardown chọn:**
AI phân tích chi tiêu, tự động phân loại giao dịch, hỗ trợ ghi chép chi tiêu, báo cáo tuần/tháng và gợi ý chi tiêu hợp lý.

---

## 2. Promise vs Reality

### Product hứa gì?
MoMo định vị mình là **Trợ thủ Tài chính với AI**, giúp người dùng “làm được nhiều hơn với tiền”. Với tính năng quản lý chi tiêu, MoMo hứa rằng AI có thể ghi chép chi tiêu tự động, phân loại giao dịch, tạo báo cáo tuần/tháng và gợi ý chi tiêu hợp lý. Nguồn public của MoMo cũng mô tả tính năng quản lý chi tiêu có “tự động phân loại nhiều giao dịch”, “quản chi tiêu trong và ngoài MoMo”, “báo cáo chi tiêu chi tiết, dễ hiểu” và “hỗ trợ bởi trợ thủ A.I thông minh”.

### User nào được hứa sẽ được giúp?
User chính là người dùng MoMo có nhu cầu:

- biết mình đang tiêu tiền vào đâu;
- kiểm soát chi tiêu theo tuần/tháng;
- không muốn tự ghi chép thủ công;
- muốn được nhắc khi sắp tiêu quá tay;
- muốn có gợi ý tiết kiệm cụ thể dựa trên hành vi chi tiêu.

### Kỳ vọng AI làm được task nào?
Tôi kỳ vọng Moni có thể làm 4 việc:

1. Tự động phân loại giao dịch đúng danh mục.
2. Phân biệt giao dịch thật sự là chi tiêu với giao dịch không nên tính vào chi tiêu, ví dụ hoàn tiền, chuyển hộ, chia bill, nạp/rút ví.
3. Khi không chắc, hỏi lại user thay vì tự đoán.
4. Khi user sửa danh mục, hệ thống ghi nhớ để lần sau phân loại tốt hơn.

### Reality / điểm gãy có khả năng xuất hiện
Điểm gãy chính nằm ở **correction path**: nếu AI phân loại sai giao dịch nhưng user không sửa được nhanh, hoặc sửa xong mà hệ thống không học lại, thì báo cáo chi tiêu sẽ mất độ tin cậy.

Với quản lý chi tiêu cá nhân, chỉ cần một vài giao dịch bị phân loại sai, user có thể không còn tin báo cáo nữa.

---

## 3. Evidence / Observation cụ thể

### Evidence từ product promise
MoMo public promise rằng quản lý chi tiêu có:

- ghi chép chi tiêu tự động bằng AI;
- phân loại tự động theo danh mục rõ ràng;
- báo cáo tuần/tháng trực quan;
- gợi ý chi tiêu hợp lý từ trợ lý AI.

### Observation dùng cho teardown
Do không đăng nhập vào tài khoản MoMo cá nhân trong bài nộp này, observation được ghi theo dạng kiểm thử sản phẩm cần thực hiện trên app thật:

**Prompt/Input nên thử trong Moni:**

1. “Tháng này tôi tiêu nhiều nhất vào khoản nào?”
2. “Khoản chuyển tiền cho bạn có tính là chi tiêu không?”
3. “Tôi có đang tiêu quá tay không?”
4. “Gợi ý giúp tôi tiết kiệm 1 triệu trong tháng này.”
5. “Sửa giao dịch Grab này thành Ăn uống.”

**Observation cần chụp screenshot khi dùng app thật:**

- màn hình Moni / Quản lý chi tiêu;
- màn hình báo cáo chi tiêu theo danh mục;
- màn hình giao dịch bị phân loại sai hoặc cần sửa;
- màn hình sửa danh mục nếu có;
- màn hình AI trả lời hoặc đưa insight.

**Observation chính cho finding:**
Feature quản lý chi tiêu chỉ đáng tin nếu user có thể thấy giao dịch nguồn, sửa phân loại sai, và correction được lưu lại. Nếu không, AI chỉ tạo báo cáo “có vẻ thông minh” nhưng không đủ đáng tin để user dùng lâu dài.

---

## 4. Flow as-is

```
User mở MoMo
→ Vào Moni / Quản lý chi tiêu
→ AI đọc dữ liệu giao dịch
→ AI tự phân loại giao dịch
→ AI tạo báo cáo / insight / gợi ý
→ User đọc kết quả
→ Nếu thấy sai, user phải tự tìm cách sửa hoặc bỏ qua
```

### Điểm gãy trong flow as-is
Điểm gãy nằm ở đoạn:

```
AI tự phân loại giao dịch
→ User thấy báo cáo
→ User phát hiện sai
→ Không rõ sửa thế nào / sửa xong AI có học không
```
Vấn đề không chỉ là “AI phân loại sai”. Vấn đề product thật sự là: **user không có recovery path đủ rõ để sửa lỗi và khôi phục niềm tin**.

---

## 5. Vẽ 4 paths

### Path 1 — Happy path
**Câu hỏi:** Khi AI đúng và tự tin, user thấy gì?

**Trigger:**
User hỏi:

> “Tháng này tôi tiêu nhiều nhất vào khoản nào?”
**AI/Product behavior tốt:**
Moni trả lời:

> “Tháng này bạn tiêu nhiều nhất vào Ăn uống: 3.200.000đ, tăng 25% so với tháng trước. Ba giao dịch lớn nhất là GrabFood, Highlands và Kichi Kichi.”
**User value:**
User hiểu nhanh tiền đi đâu, không cần tự cộng giao dịch.

**Yêu cầu UX:**
Insight nên có nút:

> “Xem giao dịch liên quan”

dể user biết kết luận của AI đến từ đâu.

---

### Path 2 — Low-confidence path
**Câu hỏi:** Khi AI không chắc, hệ thống có hỏi lại, show options hoặc chuyển người không?

**Trigger:**
User có giao dịch mơ hồ:

> “Chuyển khoản 700.000đ cho Minh”
AI không biết đây là:

- trả nợ;
- chia bill;
- chuyển hộ;
- quà tặng;
- chi tiêu cá nhân;
- giao dịch không nên tính vào chi tiêu.

**Failure hiện tại có thể xảy ra:**
AI tự phân loại vào “Khác” hoặc “Chi tiêu cá nhân” mà không hỏi lại.

**Impact:**
Báo cáo chi tiêu sai. User không biết giao dịch nào đang bị AI đoán mò.

**Product decision:**
Với giao dịch low-confidence, Moni cần gắn nhãn:

> “Cần xác nhận”

và đưa 2–3 lựa chọn:

- Chi tiêu cá nhân;
- Chuyển hộ;
- Chia bill;
- Không tính vào chi tiêu.

---

### Path 3 — Failure path
**Câu hỏi:** Khi AI sai, user biết bằng cách nào và sửa thế nào?

**Trigger:**
AI phân loại sai giao dịch.

Ví dụ:

- Hoàn tiền bị tính là thu nhập.
- Chuyển hộ bị tính là chi tiêu.
- Chia bill bị tính toàn bộ vào chi tiêu cá nhân.
- GrabFood bị xếp vào Di chuyển.
- Nạp/rút ví bị tính nhầm là chi tiêu.

**Failure:**
AI tạo báo cáo tài chính sai.

**Impact:**
User mất niềm tin vào báo cáo. Một khi user không tin dữ liệu phân loại, các insight phía sau như “tiêu quá tay” hoặc “nên tiết kiệm khoản nào” cũng không còn giá trị.

**Product decision:**
Phải có các lựa chọn sửa nhanh:

- Sửa danh mục;
- Không tính vào chi tiêu;
- Đây là hoàn tiền;
- Đây là chuyển hộ;
- Đây là chia bill;
- Đây là giao dịch công việc.

---

### Path 4 — Correction path
**Câu hỏi:** Khi user sửa, correction có được lưu/log/học lại không hay biến mất?

**Trigger:**
User thấy giao dịch Grab bị xếp sai.

Ví dụ:

> Grab được xếp vào “Di chuyển”, nhưng thực tế là GrabFood nên thuộc “Ăn uống”.
**Failure nếu correction path yếu:**
User sửa xong một giao dịch, nhưng lần sau giao dịch tương tự vẫn sai.

**Impact:**
User cảm thấy AI không học. Việc sửa lỗi trở thành thao tác thủ công lặp lại. Data flywheel không hình thành.

**Product decision:**
Sau khi user sửa, Moni nên hỏi:

> “Áp dụng cho các giao dịch tương tự sau này không?”

Hệ thống cần lưu correction log gồm:

- giao dịch gốc;
- danh mục AI dự đoán;
- confidence;
- danh mục user sửa;
- merchant;
- số tiền;
- thời điểm sửa;
- user chọn “áp dụng lần sau” hay không.

---

## 6. Finding note

### Finding chính

```
Khi user có giao dịch mơ hồ như chuyển hộ, chia bill, hoàn tiền hoặc merchant đa nghĩa như Grab,
AI có thể tự phân loại sai vào chi tiêu cá nhân,
hậu quả là báo cáo chi tiêu sai và user mất niềm tin vào Moni.
Lỗi thuộc layer Intent + Data/Tool + UX Recovery.
Nên sửa bằng low-confidence path và correction loop: gắn nhãn “Cần xác nhận”, cho user sửa danh mục nhanh, thêm “Không tính vào chi tiêu”, và lưu correction log để AI học lại.
```

### Vì sao đây không chỉ là bug?
Nếu chỉ ghi “AI phân loại sai”, team sẽ sửa từng lỗi nhỏ.
Nhưng nếu nhìn theo framework product, bug này cho thấy một quyết định lớn hơn:

> Moni chưa nên tăng automation sang tư vấn tài chính sâu nếu dữ liệu phân loại chi tiêu chưa đáng tin.

Product decision đúng là:

> Ưu tiên xây correction loop và trust layer trước, sau đó mới tăng automation lên gợi ý tiết kiệm cá nhân hóa.

---

## 7. Sketch as-is / to-be

### As-is sketch

```
┌────────────────────┐
│ User mở MoMo       │
└─────────┬──────────┘
          ↓
┌────────────────────┐
│ Vào Moni / QLCT    │
└─────────┬──────────┘
          ↓
┌────────────────────┐
│ AI đọc giao dịch   │
└─────────┬──────────┘
          ↓
┌────────────────────┐
│ AI tự phân loại    │
└─────────┬──────────┘
          ↓
┌────────────────────┐
│ Báo cáo chi tiêu   │
└─────────┬──────────┘
          ↓
┌────────────────────────────────┐
│ User thấy sai                  │
│ Ví dụ: chuyển hộ bị tính chi   │
└─────────┬──────────────────────┘
          ↓
┌────────────────────────────────┐
│ Điểm gãy:                      │
│ - không rõ AI chắc hay không   │
│ - sửa lỗi chưa nổi bật         │
│ - không rõ AI có học lại không │
└────────────────────────────────┘
```

---

### To-be sketch

```
┌────────────────────┐
│ User mở MoMo       │
└─────────┬──────────┘
          ↓
┌────────────────────┐
│ Vào Moni / QLCT    │
└─────────┬──────────┘
          ↓
┌──────────────────────────────┐
│ AI đọc giao dịch             │
│ + phân loại theo confidence  │
└─────────┬────────────────────┘
          ↓
┌──────────────────────────────┐
│ Nếu confidence cao            │
│ → đưa vào báo cáo             │
└─────────┬────────────────────┘
          ↓
┌──────────────────────────────┐
│ Nếu confidence thấp           │
│ → gắn nhãn “Cần xác nhận”     │
│ → đưa 2-3 lựa chọn danh mục   │
└─────────┬────────────────────┘
          ↓
┌──────────────────────────────┐
│ User sửa nhanh                │
│ - Sửa danh mục                │
│ - Không tính vào chi tiêu     │
│ - Hoàn tiền / chuyển hộ       │
└─────────┬────────────────────┘
          ↓
┌──────────────────────────────┐
│ App hỏi:                      │
│ “Áp dụng cho lần sau không?”  │
└─────────┬────────────────────┘
          ↓
┌──────────────────────────────┐
│ Lưu correction log            │
│ → cập nhật báo cáo            │
│ → tạo eval/training signal    │
└──────────────────────────────┘
```

---

## 8. Map finding vào SPEC

### SPEC update sentence
Finding này sẽ đổi SPEC theo hướng: **Moni phải có low-confidence path và correction loop cho phân loại giao dịch trước khi tăng automation sang tư vấn tài chính cá nhân hóa.**

### Ghi vào SPEC như sau
SPEC fieldNội dung cần thêmRequirementVới giao dịch confidence thấp, AI không được tự đưa vào báo cáo chính mà phải gắn nhãn “Cần xác nhận”.UX RecoveryUser sửa danh mục trong tối đa 2 thao tác. Có lựa chọn “Không tính vào chi tiêu”.4 pathsBổ sung low-confidence path và correction path rõ ràng.Failure modesTop failure mode: giao dịch mơ hồ bị tính nhầm là chi tiêu cá nhân.Learning signalLưu correction log: category AI đoán, category user sửa, merchant, confidence, thời điểm sửa.EvalĐo category accuracy, correction completion rate, repeat error rate theo merchant/category.Automation ladderGiữ ở Level 2: AI phân loại + user sửa/duyệt. Chưa lên Level 4/5.

---

## 9. Top failure modes

TriggerFailureImpactMitigationChuyển tiền cho bạn bèAI tính là chi tiêu cá nhânBáo cáo tháng saiHỏi lại: chuyển hộ, chia bill, quà tặng hay chi tiêu?Hoàn tiền / cashbackAI tính là thu nhập hoặc chi tiêu âm saiSai dòng tiềnTự nhận diện refund hoặc yêu cầu user xác nhậnMerchant đa nghĩa như GrabXếp sai Ăn uống / Di chuyểnSai danh mục lớnDựa vào metadata + correction theo merchantNạp/rút víTính nhầm là chi tiêuTổng chi tiêu bị phóng đạiThêm rule “không tính vào chi tiêu”Giao dịch công việcTính vào chi tiêu cá nhânInsight cá nhân saiThêm tag “Công việc / reimbursable”

---

## 10. Metrics / Signals

MetricMục tiêuCategory accuracy≥ 85% với giao dịch phổ biếnLow-confidence confirmation rate≥ 70% giao dịch mơ hồ được user xác nhậnCorrection completion rate≥ 60% user bắt đầu sửa thì hoàn tấtRepeat error rateGiảm theo tuần theo merchant/categoryInsight usefulness rate≥ 50% user đánh dấu insight hữu íchDuplicate query rateGiảm nếu AI có trạng thái xử lý rõ

---

## 11. Product decision cuối cùng

**Product decision:**
Không nên ưu tiên để Moni tự động tư vấn tài chính sâu hơn ngay. Trước tiên cần cải thiện trust layer cho dữ liệu chi tiêu bằng low-confidence path và correction loop.

**Lý do:**
Nếu phân loại chi tiêu chưa đáng tin, mọi insight như “bạn tiêu quá tay”, “nên tiết kiệm khoản này”, hoặc “tháng sau nên đặt ngân sách bao nhiêu” đều yếu. Trust phải được xây trước automation.

**Decision cụ thể:**

- Thêm nhãn “Cần xác nhận” cho giao dịch mơ hồ.
- Thêm nút “Sửa danh mục”.
- Thêm lựa chọn “Không tính vào chi tiêu”.
- Thêm câu hỏi “Áp dụng cho giao dịch tương tự sau này không?”
- Lưu correction log.
- Đo repeat error rate trước khi tăng automation.
