# 1. Tổng quan
Khác với yêu cầu 1 chỉ tập trung vào các NSCs, yêu cầu 2 cover toàn bộ thành phần hệ thống trong tổ chức. Yêu cầu này bao gồm các yêu cầu về triển khai, cấu hình hệ thống phù hợp, nhầm tăng cường bảo mật trên từng thành phần hệ thống.
# 2. Yêu cầu
## 2.2 Cấu hình và quản lý an toàn các thành phần hệ thống
### 2.2.1
Configuration standards are developed, implemented, and maintained to:
• Cover all system components.
• Address all known security vulnerabilities.
• Be consistent with industry-accepted system hardening standards or vendor hardening recommendations.
• Be updated as new vulnerability issues are identified, as defined in Requirement 6.3.1.
• Be applied when new systems are configured and verified as in place before or immediately after a system component is connected to a production environment.

Khi xây dựng, vận hành hệ thống cần cần có các tiêu chuẩn cấu hình quy định từ các bước thiết lập ban đầu, đến kiểm tra thử nghiệm (nếu có) và khi đưa vào hệ thống thực tế. Từng loại hệ thống nên có riêng một tiêu chuẩn để đảm bảo việc cấu hình phù hợp cho loại hệ thống và chức năng của hệ thống.
Các tiêu chuẩn này nên nhất quán với các khuyến nghị hardening của ngành và các khuyến nghị hardening của nhà cung cấp. Nhân sự chịu trách nhiệm nên thường xuyên cập nhật các hướng dẫn mới liên quan đến nâng cao bảo mật hệ thống để áp dụng vào tiêu chuẩn cấu hình của tổ chức. Các cuộc tấn công luôn thay đổi, nâng cấp ngày càng tinh vi, bên cạnh đó cũng xuất hiện nhiều công nghệ mới, biện pháp bảo mật mới nên việc thường xuyên cập nhật tình hình an ninh mạng và các hướng dẫn, khuyến nghị bảo mật là cần thiết để xây dựng tiêu chuẩn đạt hiệu quả bảo mật liên tục.
Mỗi loại hệ thống cần có một loại tiêu chuẩn cấu hình riêng, vì từng loại hệ thống mang những chức năng riêng biệt, cấu hình cũng cần phải phù hợp để đảm bảo tính hiệu quả của cấu hình, và tính bảo mật đối với thành phần hệ thống đó.
Có nhiều nguồn đưa ra các hướng dẫn về tiêu chuẩn cấu hình nổi tiếng như NIST, ISO, CIS, Cloud Security Alliance khi soạn thảo hoặc review các tiêu chuẩn cấu hình nên tham khảo các hướng dẫn trên cùng với các khuyến nghị từ nhà cung cấp thành phần hệ thống, thiết bị.
### 2.2.2
> Vendor default accounts are managed as follows:
> • If the vendor default account(s) will be used, the default password is changed per Requirement 8.3.6.
> • If the vendor default account(s) will not be used, the account is removed or disabled.

Tiêu chuẩn yêu cầu nếu sử dụng tài khoản mặc định, thì mật khẩu phải được thay đổi là mật khẩu xác thực mạnh, ít nhất 12 ký tự (hoặc 8 kí tự nếu hệ thống không hỗ trợ 12 ký tự), bao gồm các kí tự số và chữ cái. Đối với các tài khoản mặc định không sử dụng phải vô hiệu hoặc hoặc xóa đi.
Các tài khoản mặc định, thông tin bao gồm user IDs, mật khẩu và các định danh xác thực khác được các nhà cung cấp công khai trên website, tài liệu hướng dẫn, hoặc trên chính thiết bị. Các thông tin luôn này được biết đến rộng rãi, hoặc ít nhất là những cá nhân muốn tìm hiểu. Việc sử dụng các tài khoản này mà không có hành động thay đổi các thông tin trên mạng lại rủi ro cao cho tổ chức, khi tài khoản đáng ra phải được bí mật thì bất kỳ ai, đặc biệt là các cá nhân có ý đồ xấu đều biết, dẫn đến việc nếu bị xâm nhập, kẻ tấn công có sẵn một tài khoản để thao tác trên hệ thống. Tương tự như với các tài khoản mặc định không sử dụng nhưng tổ chức không có hành động xóa hoặc vô hiệu hóa, cũng không khác việc cung cấp cho các cá nhân có ý xấu một tài khoản để thao tác trên hệ thống, đặc biệt là những tài khoản mặc định có đặc quyền cao.
### 2.2.3
> Primary functions requiring different security levels are managed as follows:
> • Only one primary function exists on a system component,
> OR
> • Primary functions with differing security levels that exist on the same system component are isolated from each other,
> OR
> • Primary functions with differing security levels on the same system component are all secured to the level required by the function with the highest security need.

Một hệ thống là một tập hợp của các dịch vụ, trình nền, giao thức chuyên biệt để hỗ trợ cho một hoặc vài chức năng chính của hệ thống. Các cấu hình bảo mật phải phù hợp để hệ thống có khả năng thực hiện hiệu quả các chức năng chính đó, mà không ảnh hưởng đến độ an toàn của hệ thống.
Trong hệ thống thường sẽ có những hệ thống có thể được truy cập trực tiếp từ bên ngoài (DNS server, web server, ...), cũng có những hệ thống mà tổ chức không muốn phơi bày ra ngoài (database server, application server). Yêu cầu này mục đích là để những hệ thống có các chức năng với mức độ an toàn khác nhau vận hành hiệu quả, không để những chức năng có nhu cầu an toàn thấp có thể ảnh hưởng đến chức năng có nhu cầu an toàn cao hơn.
Lý tưởng nhất, tổ chức nên triển khai một chức năng chính trên một thành phần hệ thống. Nếu cùng tồn tại trên một thành phần hệ thống, thì phải cô lập với nhau, hoặc phải được bảo mật với chức năng chính có nhu cầu bảo mật cao nhất.
Các công nghệ hỗ trợ cô lập có thể bao gồm: ảo hóa các máy chủ, container, sandbox, ...
### 2.2.4
> Only necessary services, protocols, daemons, and functions are enabled, and all unnecessary functionality is removed or disabled.

Chỉ kích hoạt, sử dụng những dịch vụ, giao thức, trình nền và chức năng cần thiết, tất cả các chức năng không cần thiết khác phải được gỡ bỏ hoặc vô hiệu hóa. Các chức năng cần thiết có thể bao gồm các chức năng không an toàn. Trên các hệ thống có thể mặc định bật những chức năng không cần thiết, việc tắt các chức năng này làm giải bề mặt có thể tấn công.
Các chức năng có thể bao gồm nhưng không giới hạn: scripts, drivers, features, subsystems, ile systems, interfaces (USB and Bluetooth), and nnecessary web servers.
### 2.2.5
> If any insecure services, protocols, or daemons are present:
> • Business justification is documented.
> • Additional security features are documented and implemented that reduce the risk of using insecure services, protocols, or daemons.

Tổ chức cần cân nhắc rủi ro của việc sử dụng các dịch vụ, giao thức, trình nền không an toàn. Khi sử dụng cần phải có các tính năng bảo mật bổ sung để giảm thiểu rủi ro.
Có một vài giải pháp nhà cung cấp cung cấp các chức năng bảo mật bổ sung để hỗ trợ bảo mật thêm các tiến trình không an toàn, tổ chức khi thiết lập sử dụng các dịch vụ, giao thức, trình nền không an toàn nên tham khảo tài liệu, hướng dẫn từ nhà cung cấp, hoặc các khuyến nghị bảo mật để giảm thiểu rủi ro.
### 2.2.6
> System security parameters are configured to prevent misuse.

Các tham số bảo mật của từng thành phần hệ thống phụ thuộc vào chức năng mà nó cung cấp, hãng sản xuất, ... Ngoài việc đảm bảo bảo mật cho hệ thống, việc cấu hình phù hợp còn tăng hiệu suất hệ thống, đảm bảo hệ thống công nghệ thông tin vận hành hiệu quả.
Để có thể cấu hình các tham số phù hợp, an toàn, nhân sự chịu trách nhiệm cần phải có kiến thức về các tham số này để áp dụng vào hệ thống. Khi cấu hình các tham số này, nhân sự nên tham khảo các khuyến nghị bảo mật từ nhà cung cấp hoặc các khuyến nghị của ngành, đồng thời xem xét điểm yếu, thực tế của hệ thống để cấu hình phù hợp.
### 2.2.7 
> All non-console administrative access is encrypted using strong cryptography.

Việc mã hóa mạnh các quyền truy cập quản trị non-console với mã hóa mạnh giúp chống lại các tác nhân nghe lén trong mạng, đặc biệt khi sử dụng các mạng công cộng. Các truy cập quản trị non-console có thể bao gồm truy cập dựa trên giao diện trình duyệt web và APIs.
## 2.3 Môi trường không dây được cấu hình và quản lý an toàn
### 2.3.1 
> For wireless environments connected to the CDE or transmitting account data, all wireless vendor defaults are changed at installation or are confirmed to be secure, including but not limited to:
> • Default wireless encryption keys.
> • Passwords on wireless access points.
> • SNMP defaults.
> • Any other security-related wireless vendor defaults.

Khi sử dụng môi trường mạng không dây để kết nối đến CDE hoặc để truyền tải dữ liệu tài khoản, tất cả cả các mặc định nhà cung cấp cần phải được thay đổi hoặc được xác nhận là an toàn bao gồm các khóa không dây mặc đinh, các mật khẩu của các điểm truy cập không dây, các mặc định SNMP, hoặc các mặc định liên quan đến bảo mật khác. Nếu không được thay đổi phù hợp, các kẻ tấn công dễ dàng xâm nhập vào mạng, bắt các lưu lượng dẫn đến rò rỉ thông tin hoặc gián đoạn mạng.
Đối với mật khẩu của mạng không dây, cần có độ xác thực đủ mạnh để chống lại các tấn công brute force.
### 2.3.2
> For wireless environments connected to the CDE or transmitting account data, wireless encryption keys are changed as follows:
> • Whenever personnel with knowledge of the key leave the company or the role for which the knowledge was necessary.
> • Whenever a key is suspected of or known to be compromised.

Yêu cầu này nói về khóa mã hóa của mạng không dây có kết nối đến CDE hoặc truyền tải dữ liệu tài khoản. Các khóa này cần phải được thay đổi khi có nghi ngờ bị xâm phạm, hoặc biết rõ bị xâm phạm, và nên được quản lý theo kế hoạch phản ứng sự cố của doanh nghiệp. 
Đối với nhân sự có hiểu biết về khóa, khi nhân sự này thay đổi vị trí, vai trò hoặc khi nhân sự nghỉ việc, cũng cần phải thay đổi. Việc thay đổi này giúp tổ chức giới hạn tối thiểu việc có hiểu biết về khóa theo bussiness need to know.
