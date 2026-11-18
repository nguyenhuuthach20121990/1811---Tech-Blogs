Conversation Log
Quy chuẩn Conventional Commits là gì

Conventional Commits là một quy chuẩn (convention) định dạng commit message trong Git nhằm giúp lịch sử commit trở nên rõ ràng, nhất quán và máy tính có thể đọc/phân tích tự động được. Quy chuẩn này bám sát vào cách đánh số phiên bản theo Semantic Versioning (SemVer).

1. Cấu trúc cơ bản của commit message

Một commit message theo chuẩn có cấu trúc như sau:

text
<type>[scope tùy chọn]: <mô tả ngắn>
[nội dung chi tiết - body (tùy chọn)]
[footer (tùy chọn)]
Type: Mục đích/loại thay đổi của commit (bắt buộc).
Scope: Phạm vi ảnh hưởng của thay đổi (đặt trong ngoặc đơn, không bắt buộc, ví dụ: auth, api, ui).
Description: Tóm tắt ngắn gọn thay đổi (viết ở thể hiện tại, không viết hoa chữ đầu, không kết thúc bằng dấu chấm).
Body: Mô tả chi tiết hơn về ngữ cảnh hoặc lý do thay đổi (nếu cần).
Footer: Thông tin liên kết (như ID issue/PR đóng lại Closes #123) hoặc cảnh báo thay đổi tương thích (BREAKING CHANGE).
2. Các type phổ biến
Type	Ý nghĩa	Ảnh hưởng SemVer
feat	Thêm tính năng mới cho người dùng	MINOR (0.X.0)
fix	Sửa lỗi (bug fix)	PATCH (0.0.X)
docs	Thêm/sửa tài liệu (README, comments...)	Không đổi version
style	Format code, thụt dòng, dấu chấm phẩy... (không đổi logic)	Không đổi version
refactor	Tái cấu trúc code (không fix bug, không thêm feature)	Không đổi version
perf	Cải thiện hiệu năng (performance)	Không đổi version (hoặc PATCH)
test	Thêm hoặc sửa test case	Không đổi version
build	Thay đổi hệ thống build hoặc dependencies (npm, yarn...)	Không đổi version
ci	Thay đổi cấu hình CI/CD (GitHub Actions, GitLab CI...)	Không đổi version
chore	Các công việc bảo trì vặt khác	Không đổi version
3. Quy ước về Breaking Changes (MAJOR)

Khi có thay đổi gây mất tương thích ngược (breaking changes):

Thêm dấu ! ngay trước dấu hai chấm :.
Hoặc ghi chú BREAKING CHANGE: <mô tả> ở phần footer.
4. Một số ví dụ cụ thể

Commit đơn giản (tính năng mới):

text
feat: allow user to login with Google account

Commit có scope:

text
fix(navbar): fix menu collapse on mobile devices

Commit có body và footer đóng issue:

text
fix(checkout): resolve price calculation with discount code
The discount voucher was being applied after VAT calculation instead of before.
Closes #402

Commit có Breaking Change:

text
feat(api)!: remove deprecated v1 user endpoint
BREAKING CHANGE: /api/v1/users is no longer supported, use /api/v2/users instead.
5. Lợi ích khi sử dụng Conventional Commits
Tự động sinh CHANGELOG: Các công cụ (như standard-version, semantic-release) có thể tự đọc commit để xuất changelog đầy đủ theo ngày/phiên bản.
Tự động nâng phiên bản (Semantic Versioning): Hệ thống CI/CD tự nhận biết nên tăng bản PATCH, MINOR hay MAJOR.
Lịch sử Git rõ ràng: Đồng nghiệp dễ dàng hiểu commit làm gì mà không cần đọc từng dòng code.
Hỗ trợ tìm kiếm: Dễ dàng lọc log bằng git log --grep="^feat" hoặc git log --grep="^fix".
Sự khác nhau giữa <section> và <article> là gì, nên bọc thẻ nào bên trong thẻ nào?

Trong HTML5, sự khác biệt lớn nhất giữa <article> và <section> nằm ở tính độc lập của nội dung.

1. Phân biệt <article> và <section>
Tiêu chí	Thẻ <article>	Thẻ <section>
Bản chất	Đại diện cho một khối nội dung độc lập, tự trọn vẹn (self-contained).	Đại diện cho một phần/phân đoạn theo chủ đề của một tổng thể lớn hơn.
Quy tắc kiểm tra	Nếu tách nội dung đó ra và đặt sang trang web khác, gửi qua RSS hay email mà người đọc vẫn hiểu đầy đủ ý nghĩa 
→
→ Dùng <article>.	Nếu tách riêng ra sẽ bị mất ngữ cảnh, khó hiểu nếu không có phần còn lại của trang 
→
→ Dùng <section>.
Ví dụ điển hình	Bài viết blog, tin tức báo chí, một comment, thẻ sản phẩm, bài post diễn đàn.	Phần "Giới thiệu", "Tính năng", "Liên hệ", "Dịch vụ" trên Landing Page; hoặc các chương trong một bài viết.
Tiêu đề (<h1>-<h6>)	Hầu như luôn có tiêu đề riêng.	Tiêu chuẩn HTML khuyến nghị nên có ít nhất một thẻ tiêu đề để định danh chủ đề của section.
2. Nên bọc thẻ nào bên trong thẻ nào?

Câu trả lời là: Cả hai cách đều hoàn toàn hợp lệ theo chuẩn HTML5, việc chọn cách nào phụ thuộc hoàn toàn vào cấu trúc nội dung của bạn.

Trường hợp 1: <section> bọc nhiều <article> (Rất phổ biến)

Dùng khi bạn có một phân đoạn trên trang nhóm các nội dung độc lập lại với nhau (ví dụ: Trang chủ có section "Bài viết mới nhất" hoặc "Sản phẩm nổi bật").

html
<!-- Phân đoạn: Danh sách tin tức -->
<section class="latest-news">
    <h2>Tin tức mới nhất</h2>
    <!-- Từng bài viết bên trong là một article độc lập -->
    <article>
        <h3>Cách học HTML5 hiệu quả</h3>
        <p>Tóm tắt bài viết...</p>
    </article>
    <article>
        <h3>Semantic HTML là gì?</h3>
        <p>Tóm tắt bài viết...</p>
    </article>
</section>
Trường hợp 2: <article> bọc nhiều <section> (Cũng rất phổ biến)

Dùng cho một nội dung độc lập lớn (như một bài blog dài, tài liệu hướng dẫn) được chia nhỏ thành nhiều phần/chương theo từng chủ đề con.

html
<!-- Cả bài viết là một article độc lập -->
<article class="blog-post">
    <h1>Hướng dẫn lập trình Web cơ bản</h1>
    
    <!-- Phần 1 của bài viết -->
    <section>
        <h2>1. Tổng quan về HTML</h2>
        <p>Nội dung giới thiệu HTML...</p>
    </section>
    <!-- Phần 2 của bài viết -->
    <section>
        <h2>2. Làm quen với CSS</h2>
        <p>Nội dung giới thiệu CSS...</p>
    </section>
</article>
Trường hợp 3: <article> lồng trong <article>

HTML5 cũng cho phép lồng article con vào article cha. Thường dùng nhất cho khu vực bình luận (comments) của một bài viết:

html
<article class="post">
    <h1>Tiêu đề bài viết</h1>
    <p>Nội dung bài viết...</p>
    <section class="comments">
        <h3>Bình luận</h3>
        <!-- Mỗi bình luận có thể xem là một article độc lập của tác giả bình luận -->
        <article class="comment">
            <p>Bài viết rất hay!</p>
            <small>Bởi: Nguyễn Văn A</small>
        </article>
    </section>
</article>
Tóm lại mẹo ghi nhớ:
Hỏi: "Khối này mang sang chỗ khác đọc riêng lẻ có hiểu không?"
Có: Dùng <article>.
Không: Dùng <section> (để gom nhóm theo chủ đề) hoặc <div> (chỉ để phục vụ CSS/layout thuần túy không mang ý nghĩa ngữ nghĩa).
Lồng thẻ nào vào thẻ nào là tùy thuộc vào cấu trúc dữ liệu: Trang chứa các bài viết 
→
→ <section> bọc <article>; Bài viết chia nhiều chương 
→
→ <article> bọc <section>.