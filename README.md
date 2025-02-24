# Mẫu Ứng Dụng Chính Phủ Điện Tử

## Mục Lục

-   [Tổng Quan](#tổng-quan)
-   [Cấu Trúc Dự Án](#cấu-trúc-dự-án)
-   [Quản Lý Trạng Thái](#quản-lý-trạng-thái)
-   [Cài Đặt](#cài-đặt)
-   [Cấu Hình](#cấu-hình)
-   [Các Lệnh Script](#các-lệnh-script)
-   [Bản Quyền](#bản-quyền)

## Tổng Quan

Mẫu cho Mini App Chính Phủ Điện Tử trên nền tảng Zalo

### Ảnh chụp màn hình

|                                                                              |                                                                              |                                                                              |
| :--------------------------------------------------------------------------: | :--------------------------------------------------------------------------: | :--------------------------------------------------------------------------: |
| <img width="1604" alt="ảnh chụp màn hình" src="./readme-assets/screen1.png"> | <img width="1604" alt="ảnh chụp màn hình" src="./readme-assets/screen2.png"> | <img width="1604" alt="ảnh chụp màn hình" src="./readme-assets/screen3.png"> |
| <img width="1604" alt="ảnh chụp màn hình" src="./readme-assets/screen4.png"> | <img width="1604" alt="ảnh chụp màn hình" src="./readme-assets/screen5.png"> | <img width="1604" alt="ảnh chụp màn hình" src="./readme-assets/screen6.png"> |

### Demo

Quét mã QR này bằng Zalo để xem trước Mini App mẫu

![QR!](/readme-assets/qr.png)

## Cấu Trúc Dự Án

Dự án tuân theo một cấu trúc cụ thể để tổ chức mã nguồn. Dưới đây là tổng quan về các thư mục chính và nội dung của chúng:

```shell
.
├── src
│   ├── components
│   │   ├── UIComponent1
│   │   │   ├── index.ts
│   │   │   └── UIComponent1.tsx
│   │   ├── UIComponent2
│   │   │   ├── index.ts
│   │   │   └── UIComponent2.tsx
│   │   └── ...
│   ├── services
│   │   ├── services.ts
│   │   ├── services.mock.ts
│   │   └── zalo.ts
│   ├── mock
│   │   ├── db.json
│   ├── pages
│   │   ├── [PageName]
│   │   │   ├── index.ts
│   │   │   └── [PageName].tsx
│   │   ├── Page1
│   │   │   ├── index.ts
│   │   │   └── Page1.tsx
│   │   ├── Page2
│   │   │   ├── index.ts
│   │   │   ├── Section1.tsx
│   │   │   ├── Section2.tsx
│   │   │   └── Page2.tsx
│   │   └── ...
│   ├── constants
│   │   └── common.ts
│   ├── utils
│   ├── types
│   ├── css
│   │   ├── global.css
│   │   ├── tailwind.css
│   └── assets
│       ├── image1.png
│       ├── image2.png
│       └── ...
├── .env
├── .env.production
├── .env.development
├── .gitignore
├── package.json
└── README.md
```

-   **`src/components`**: Chứa các component UI và component dùng chung trong dự án.
-   **`src/pages`**: Chứa các trang và phần của trang. Mỗi trang đại diện cho một route hoặc view cụ thể của ứng dụng.
-   **`src/pages/index`**: Chứa cấu hình route cho các trang. Đây là nơi định nghĩa logic điều hướng của ứng dụng.
-   **`src/constants`**: Định nghĩa các hằng số được sử dụng trong dự án, như các endpoint API và các giá trị cấu hình khác.
-   **`env.production` và `env.development`**: Chỉnh sửa URL cơ sở API trong các file môi trường này (`VITE_BASE_URL`) dựa trên môi trường triển khai của bạn.
-   **`.env`**: Chứa các biến cấu hình cho ứng dụng. Đảm bảo cập nhật `APP_ID` trong file này.
-   **`src/utils`**: Chứa các hàm tiện ích có thể sử dụng trong toàn dự án.
-   **`src/types`**: Chứa các khai báo kiểu dữ liệu để đảm bảo type safety và tài liệu hóa mã nguồn tốt hơn.
-   **`src/css`**: Chứa các style CSS toàn cục và cấu hình Tailwind CSS.
-   **`src/assets`**: Chứa các tài nguyên tĩnh như hình ảnh, font chữ và các tài nguyên khác được sử dụng trong dự án.
-   **`src/mock`**: Dữ liệu giả để kiểm thử UI
-   **`src/services`**:
    -   **`services.ts`**: File này chứa triển khai cho các cuộc gọi API service.
    -   **`services.mock.ts`**: File này được sử dụng để giả lập services trong quá trình kiểm thử UI.
    -   **`zalo.ts`**: File này chứa triển khai cho các cuộc gọi API Zalo.

## Quản Lý Trạng Thái

[Zustand](https://github.com/pmndrs/zustand) được sử dụng để quản lý trạng thái trong dự án này. Trạng thái được tổ chức thành các slice khác nhau dựa trên tính năng mà nó thuộc về. Các slice có sẵn bao gồm:

-   **`authSlice`**: Quản lý trạng thái liên quan đến xác thực.
-   **`appSlice`**: Quản lý trạng thái cấp ứng dụng, bao gồm thông báo và cài đặt giao diện.
-   **`feedbackSlice`**: Xử lý trạng thái liên quan đến phản hồi cho các tính năng tương lai.
-   **`informationGuideSlice`**: Quản lý trạng thái liên quan đến hướng dẫn cho một tính năng cụ thể.
-   **`organizationSlice`**: Xử lý trạng thái liên quan đến thông tin tổ chức cho một tính năng cụ thể.
-   **`scheduleSlice`**: Quản lý trạng thái liên quan đến lịch hẹn cho một tính năng cụ thể.

Mã nguồn quản lý trạng thái có thể được tìm thấy trong thư mục `/src/store`.

## Cài Đặt

Để cài đặt các dependencies của dự án, vui lòng thực hiện theo các bước sau:

1. Đảm bảo bạn đã cài đặt [Node.js](https://nodejs.org) trên máy tính.

2. Mở terminal hoặc command prompt và di chuyển đến thư mục gốc của dự án.

3. Chạy lệnh sau để cài đặt các dependencies của dự án bằng **yarn**:

    ```shell
    yarn install
    ```

    Nếu bạn muốn sử dụng **npm**, hãy chạy lệnh sau:

    ```shell
    npm install
    ```

    Điều này sẽ tải xuống và cài đặt tất cả các gói cần thiết được định nghĩa trong file `package.json`.

## Cấu Hình

Để cấu hình dự án cho môi trường triển khai và cài đặt ứng dụng cụ thể của bạn, hãy làm theo các hướng dẫn dưới đây:

### URL Cơ Sở API

-   Chỉnh sửa URL cơ sở API trong các file môi trường tại `env.production` và `env.development`. Tìm biến `VITE_BASE_URL` và cập nhật nó với URL phù hợp cho API backend của bạn.

### Các Endpoint API

Các endpoint API được định nghĩa trong file `src/constants/common.ts`. Sửa đổi các giá trị để phù hợp với endpoint mong muốn của bạn. Bạn có thể thay thế các giá trị của endpoint với mẫu tên_endpoints. Dưới đây là ví dụ cập nhật:

```ts
export const API = {
    GET_ORGANIZATION: "/get_organization_api",
    SEARCH_PROFILES: "/search_profiles_api",
    GET_ARTICLES: "/get_articles_api",
    FEEDBACK: "/feedback_api",
    FEEDBACK_TYPES: "/feedback_types_api",
    INFORMATION_GUIDE: "/information_guide_api",
    UPLOAD_IMAGE: "/upload_image_api",
    CREATE_SCHEDULE: "/create_schedule_api",
    GET_SCHEDULE: "/get_schedule_api",
};
```

### ID Ứng Dụng

-   Cập nhật `APP_ID` trong file `.env` với ID Zalo Mini App mong muốn.

## Các Lệnh Script

Các lệnh script sau có sẵn để chạy trong dự án:

-   **`npm start`**: Khởi chạy dự án.
-   **`npm deploy`**: Triển khai dự án.

## Bản Quyền

Dự án này thuộc sở hữu của **đội ngũ Zalo Mini App**
