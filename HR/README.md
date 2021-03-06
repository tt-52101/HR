# Tài liệu quy ước Core.FE

## **Build và commit code**

- > Trước khi commit code cần chạy lệnh để build code với môi trường product: ng build --prod
- > Mỗi người sẽ có 1 branch riêng để lập trình.
- > Mỗi lần trước khi commit sẽ thực hiện pull code từ branch develope về, tiến hành merge rồi commit code lên branch của mình và branch develop, code build lên môi trường test sẽ từ branch develope

## Quy tắc đặt tên

- Tên Class viết theo kiểu: Pascal Case (ThisWordIsInPascalCase) ví dụ: export class ConfigurationClass
- Tên "export const ..."  viết theo kiểu Camel Case (thisWordIsInCamelCase) ví dụ: export const configurationRouter

## Đặt tên trong file đa ngôn ngữ

- `src\assets\tmp\i18n\vi-VN.json`
- Quy ước chung đặt label cho các chức năng riêng
- Tên module (catalog, product…. )
- Tên chức năng (stock-warehouse, routing)
- Tên thành phần trên màn hình (label, button, grid…)
- Các thành phần phụ nếu có sẽ được thêm vào phía sau (có thể thêm đuôi nếu cần thiết)
Ví dụ: catalog.stock-warehouse.label.add: "Thêm mới", catalog.stock-warehouse.button.delete: "Xóa",
- Tham khảo các tên bắt đầu với **menu** và **app**

## Một số lưu ý chung

- Các control, message, label trên màn hình đều phải sử dụng đa ngôn ngữ
  - Với code html: {{ 'menu.account.logout' | translate }}
  - Với code TS: console.log(this.i18n.fanyi('app.setting.copyinfo'));
  - Tham khảo từ khóa tìm kiếm: setting-drawer.component

- Thư viện tham khảo:
  - <https://ng-alain.com/>
  - <https://ng.ant.design/docs/introduce/en>

- Các api chỉ trả ra dữ liệu cần thiết, hạn chế trả ra dữ liệu thừa - performance kém
  - Table dùng api riêng
  - List của combo box sẽ dùng api riêng

## Cấu trúc thư mục

```javascript
├── _mock                                       # Local Mock Data
├── src
│   ├── app
│   │   ├── core
│   │   │   ├── i18n
│   │   │   ├── net
│   │   │   │   └── default.interceptor.ts      # Default HTTP interceptor
│   │   │   ├── services
│   │   │   │   └── startup.service.ts          # Initialize project configuration
│   │   │   └── core.module.ts                  # Core module file
│   │   ├── layout                              # Layout files
│   │   ├── models                              # Models
│   │   │   ├── catalog-manager                 # Các model liên quan đến quản lý danh mục hệ thống
│   │   │   │   ├── **                          # ...
│   │   │   ├── production-manager              # Các model liên quan đến quản lý sản xuất
│   │   │   │   ├── **                          # ...
│   │   │   ├── warehouse-management            # Các model liên quan đến quản lý kho
│   │   │   │   ├── **                          # ...
│   │   │   ├── sales-manager                   # Các model liên quan đến bán hàng
│   │   │   │   ├── **                          # ...
│   │   │   ├── purchase-manager                # Các model liên quan đến mua hàng
│   │   │   │   ├── **                          # ...
│   │   │   ├── passport                        # Các model liên quan đến đăng nhập, đăng ký
│   │   │   │   ├── **                          # ...
│   │   │   ├── **                              # Business directory
│   │   │   └── index.ts                        # index file
│   │   ├── routes
│   │   │   ├── catalog-manager                 # Các chức năng liên quan đến quản lý danh mục hệ thống
│   │   │   │   ├── Danh mục Kho hàng           # ...
│   │   │   │   ├── Danh mục Địa điểm           # ...
│   │   │   │   ├── Danh mục Nhóm đơn vị        # ...
│   │   │   │   ├── Danh mục đơn vị             # ...
│   │   │   │   ├── Danh mục Công ty            # ...
│   │   │   │   ├── Danh mục Khách hàng/NCC     # ...
│   │   │   │   ├── Danh mục Nhóm hàng hoá      # ...
│   │   │   │   ├── Danh mục hàng hoá           # ...
│   │   │   │   ├── Danh mục Nhóm đơn vị tính   # ...
│   │   │   │   ├── Danh mục Đơn vị tính        # ...
│   │   │   │   ├── Danh mục Tiền tệ            # ...
│   │   │   │   ├── Danh mục Quốc gia           # ...
│   │   │   │   ├── Danh mục Thuế               # ...
│   │   │   │   ├── Danh mục Tỉnh/Thành phố     # ...
│   │   │   │   ├── Danh mục Ngày nghỉ lễ       # ...
│   │   │   │   ├── **                          # ...
│   │   │   ├── production-manager              # Các chức năng liên quan đến quản lý sản xuất
│   │   │   │   ├── Định mức nguyên vật liệu    # ...
│   │   │   │   ├── Quy trình sản xuất          # ...
│   │   │   │   ├── Công đoạn sản xuất          # ...
│   │   │   │   ├── Lệnh sản xuất               # ...
│   │   │   │   ├── Xuất NVL cho sản xuất       # ...
│   │   │   │   ├── Nhập kho thành phẩm         # ...
│   │   │   │   ├── Lệnh làm việc               # ...
│   │   │   │   ├── **                          # ...
│   │   │   ├── warehouse-management            # Các chức năng liên quan đến quản lý kho
│   │   │   │   ├── Nhập kho                    # ...
│   │   │   │   ├── Xuất kho                    # ...
│   │   │   │   ├── Điều chuyển kho nội bộ      # ...
│   │   │   │   ├── Điều chỉnh tồn kho          # ...
│   │   │   │   ├── Xuất NVL cho sản xuất       # ...
│   │   │   │   ├── Nhập kho thành phẩm         # ...
│   │   │   │   ├── Lệnh làm việc               # ...
│   │   │   │   ├── **                          # ...
│   │   │   ├── sales-manager                   # Các chức năng liên quan đến bán hàng
│   │   │   │   ├── Quản lý báo giá                     # ...
│   │   │   │   ├── Quản lý đơn bán hàng                # ...
│   │   │   │   ├── Quản lý giao hàng/Xuất hóa đơn      # ...
│   │   │   │   ├── Báo cáo                             # ...
│   │   │   │   ├── **                                  # ...
│   │   │   ├── purchase-manager                # Các chức năng liên quan đến mua hàng
│   │   │   │   ├── Quản lý báo giá mua         # ...
│   │   │   │   ├── Đơn đặt mua hàng            # ...
│   │   │   │   ├── Quản lý nhập hàng           # ...
│   │   │   │   ├── Báo cáo                     # ...
│   │   │   │   ├── **                          # ...
│   │   │   ├── **                              # Business directory
│   │   │   ├── routes.module.ts                # Business routing module
│   │   │   └── routes-routing.module.ts
│   │   ├── services                            # Services
│   │   │   ├── catalog-manager                 # Các api liên quan đến quản lý danh mục hệ thống
│   │   │   │   ├── Danh mục Kho hàng           # ...
│   │   │   │   ├── Danh mục Địa điểm           # ...
│   │   │   │   ├── Danh mục Nhóm đơn vị        # ...
│   │   │   │   ├── Danh mục đơn vị             # ...
│   │   │   │   ├── Danh mục Công ty            # ...
│   │   │   │   ├── Danh mục Khách hàng/NCC     # ...
│   │   │   │   ├── Danh mục Nhóm hàng hoá      # ...
│   │   │   │   ├── Danh mục hàng hoá           # ...
│   │   │   │   ├── Danh mục Nhóm đơn vị tính   # ...
│   │   │   │   ├── Danh mục Đơn vị tính        # ...
│   │   │   │   ├── Danh mục Tiền tệ            # ...
│   │   │   │   ├── Danh mục Quốc gia           # ...
│   │   │   │   ├── Danh mục Thuế               # ...
│   │   │   │   ├── Danh mục Tỉnh/Thành phố     # ...
│   │   │   │   ├── Danh mục Ngày nghỉ lễ       # ...
│   │   │   │   ├── **                          # ...
│   │   │   ├── production-manager              # Các api liên quan đến quản lý sản xuất
│   │   │   │   ├── Định mức nguyên vật liệu    # ...
│   │   │   │   ├── Quy trình sản xuất          # ...
│   │   │   │   ├── Công đoạn sản xuất          # ...
│   │   │   │   ├── Lệnh sản xuất               # ...
│   │   │   │   ├── Xuất NVL cho sản xuất       # ...
│   │   │   │   ├── Nhập kho thành phẩm         # ...
│   │   │   │   ├── Lệnh làm việc               # ...
│   │   │   │   ├── **                          # ...
│   │   │   ├── warehouse-management            # Các api liên quan đến quản lý kho
│   │   │   │   ├── Nhập kho                    # ...
│   │   │   │   ├── Xuất kho                    # ...
│   │   │   │   ├── Điều chuyển kho nội bộ      # ...
│   │   │   │   ├── Điều chỉnh tồn kho          # ...
│   │   │   │   ├── Xuất NVL cho sản xuất       # ...
│   │   │   │   ├── Nhập kho thành phẩm         # ...
│   │   │   │   ├── Lệnh làm việc               # ...
│   │   │   │   ├── **                          # ...
│   │   │   ├── sales-manager                   # Các api liên quan đến bán hàng
│   │   │   │   ├── Quản lý báo giá                     # ...
│   │   │   │   ├── Quản lý đơn bán hàng                # ...
│   │   │   │   ├── Quản lý giao hàng / Xuất hóa đơn    # ...
│   │   │   │   ├── Báo cáo                             # ...
│   │   │   │   ├── **                                  # ...
│   │   │   ├── purchase-manager                # Các api liên quan đến mua hàng
│   │   │   │   ├── Quản lý báo giá mua         # ...
│   │   │   │   ├── Đơn đặt mua hàng            # ...
│   │   │   │   ├── Quản lý nhập hàng           # ...
│   │   │   │   ├── Báo cáo                     # ...
│   │   │   │   ├── **                          # ...
│   │   │   ├── passport                        # Các api liên quan đến đăng nhập, đăng ký
│   │   │   │   ├── login                       # ...
│   │   │   │   ├── **                          # ...
│   │   │   ├── **                              # Business directory
│   │   │   └── index.ts                        # index file
│   │   ├── shared                              # Shared module
│   │   │   └── shared.module.ts
│   │   ├── app.component.ts                    # Root component
│   │   └── app.module.ts                       # Root module
│   │   └── delon.module.ts                     # @delon modules import
│   ├── assets                                  # Local static files
│   ├── environments                            # Environment configuration
│   ├── styles                                  # Project styles
└── └── style.less                              # Style entry
```
