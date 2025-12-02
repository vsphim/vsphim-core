# Vsphim Core

**English** | [Tiếng Việt](#tiếng-việt)

---

## English

### About

**Vsphim Core** is a powerful Laravel package for building movie/film CMS websites. It provides a complete admin panel using Backpack CRUD, with features for managing movies, episodes, categories, actors, directors, and more.

### Features

- 🎬 Complete movie management system
- 📺 Episode management with multiple streaming formats (Embed, MP4, M3U8)
- 🎭 Actor, Director, Studio, Tag management
- 📂 Category and Region taxonomy
- 🔍 SEO optimization tools
- 📊 View counter tracking (daily, weekly, monthly)
- 🎨 Theme management system
- 🔐 User and permission management
- 📱 Responsive admin panel

### Requirements

- **Laravel Framework**: 6.x, 7.x, or 8.x
- **PHP**: 7.3 or higher (8.0 recommended)
- **MySQL**: 5.7 or higher
- **Composer**: Latest version

#### PHP Configuration

Add to your `php.ini`:

```ini
max_input_vars=100000
```

### Installation

1. **Install the package** via Composer:

```bash
composer require vsphim/vsphim-core -W
```

2. **Configure your database** connection in `.env` file:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=your_database
DB_USERNAME=your_username
DB_PASSWORD=your_password
```

3. **Run the installation command**:

```bash
php artisan vsphim:install
```

This will:
- Publish migrations
- Run database migrations
- Seed initial data (settings, categories, regions, menus, permissions)
- Publish assets and views

4. **Update your User model** (`app/Models/User.php`):

```php
<?php

namespace App\Models;

use Vsphim\Core\Models\User as VsphimUser;
use Laravel\Sanctum\HasApiTokens;
use Illuminate\Notifications\Notifiable;
use Illuminate\Database\Eloquent\Factories\HasFactory;

class User extends VsphimUser
{
    use HasApiTokens, HasFactory, Notifiable;
    
    // Your custom code here
}
```

5. **Create an admin user**:

```bash
php artisan vsphim:user
```

Follow the prompts to create your first admin user.

6. **Remove the default welcome route** in `routes/web.php`:

Remove or comment out:
```php
Route::get('/', function () {
    return view('welcome');
});
```

7. **Clear cache**:

```bash
php artisan optimize:clear
```

8. **Access the admin panel**:

Visit: `http://your-domain.com/admin`

Login with the credentials you created in step 5.

### Update

To update to the latest version:

1. **Update the package**:

```bash
composer update vsphim/vsphim-core -W
```

2. **Run migrations** (if any):

```bash
php artisan vsphim:install
```

3. **Clear cache**:

```bash
php artisan optimize:clear
```

4. **Clear PHP Opcache** (if enabled on your server)

### Available Commands

#### Generate Menu

Generate menu items from categories and regions:

```bash
php artisan vsphim:menu:generate
```

#### Change Episode Domain

Change streaming domain for episodes:

```bash
php artisan vsphim:episode:change_domain_play
```

### Configuration

#### Production Environment

Update your `.env` file:

```env
APP_NAME="Your App Name"
APP_ENV=production
APP_DEBUG=false
APP_URL=https://your-domain.com
```

#### Timezone and Locale

In `config/app.php`:

```php
'timezone' => 'Asia/Ho_Chi_Minh',
'locale' => 'vi',
```

### Scheduled Tasks

To reset view counters automatically, add this to your crontab:

```bash
* * * * * cd /path/to/project && php artisan schedule:run >> /dev/null 2>&1
```

This will:
- Reset daily views at midnight
- Reset weekly views weekly
- Reset monthly views monthly

### Resources

- **Homepage**: [Vsphim.com](https://vsphim.com)
- **Add-ons**: [Vsphim Crawler](https://github.com/vsphim/vsphim-crawler)
- **Themes**: [More themes...](https://vsphim.com)

### Support

For issues, questions, or contributions, please visit our [GitHub repository](https://github.com/vsphim/vsphim-core).

### License

This package is open-sourced software licensed under the [MIT license](LICENSE.md).

---

## Tiếng Việt

### Giới thiệu

**Vsphim Core** là một package Laravel mạnh mẽ để xây dựng website CMS phim. Package cung cấp admin panel hoàn chỉnh sử dụng Backpack CRUD, với các tính năng quản lý phim, tập phim, thể loại, diễn viên, đạo diễn và nhiều hơn nữa.

### Tính năng

- 🎬 Hệ thống quản lý phim hoàn chỉnh
- 📺 Quản lý tập phim với nhiều định dạng streaming (Embed, MP4, M3U8)
- 🎭 Quản lý Diễn viên, Đạo diễn, Hãng phim, Thẻ
- 📂 Phân loại theo Thể loại và Quốc gia
- 🔍 Công cụ tối ưu SEO
- 📊 Theo dõi lượt xem (ngày, tuần, tháng)
- 🎨 Hệ thống quản lý giao diện
- 🔐 Quản lý người dùng và phân quyền
- 📱 Admin panel responsive

### Yêu cầu hệ thống

- **Laravel Framework**: 6.x, 7.x, hoặc 8.x
- **PHP**: 7.3 trở lên (khuyến nghị 8.0)
- **MySQL**: 5.7 trở lên
- **Composer**: Phiên bản mới nhất

#### Cấu hình PHP

Thêm vào file `php.ini`:

```ini
max_input_vars=100000
```

### Cài đặt

1. **Cài đặt package** qua Composer:

```bash
composer require vsphim/vsphim-core -W
```

2. **Cấu hình kết nối database** trong file `.env`:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=ten_database
DB_USERNAME=ten_nguoi_dung
DB_PASSWORD=mat_khau
```

3. **Chạy lệnh cài đặt**:

```bash
php artisan vsphim:install
```

Lệnh này sẽ:
- Publish migrations
- Chạy database migrations
- Seed dữ liệu ban đầu (settings, categories, regions, menus, permissions)
- Publish assets và views

4. **Cập nhật Model User** (`app/Models/User.php`):

```php
<?php

namespace App\Models;

use Vsphim\Core\Models\User as VsphimUser;
use Laravel\Sanctum\HasApiTokens;
use Illuminate\Notifications\Notifiable;
use Illuminate\Database\Eloquent\Factories\HasFactory;

class User extends VsphimUser
{
    use HasApiTokens, HasFactory, Notifiable;
    
    // Code tùy chỉnh của bạn ở đây
}
```

5. **Tạo user admin**:

```bash
php artisan vsphim:user
```

Làm theo hướng dẫn để tạo user admin đầu tiên.

6. **Xóa route welcome mặc định** trong `routes/web.php`:

Xóa hoặc comment dòng:
```php
Route::get('/', function () {
    return view('welcome');
});
```

7. **Xóa cache**:

```bash
php artisan optimize:clear
```

8. **Truy cập admin panel**:

Truy cập: `http://your-domain.com/admin`

Đăng nhập bằng thông tin đã tạo ở bước 5.

### Cập nhật

Để cập nhật lên phiên bản mới nhất:

1. **Cập nhật package**:

```bash
composer update vsphim/vsphim-core -W
```

2. **Chạy migrations** (nếu có):

```bash
php artisan vsphim:install
```

3. **Xóa cache**:

```bash
php artisan optimize:clear
```

4. **Xóa PHP Opcache** (nếu được bật trên server)

### Các lệnh có sẵn

#### Tạo Menu

Tạo menu từ categories và regions:

```bash
php artisan vsphim:menu:generate
```

#### Đổi Domain Episode

Đổi domain streaming cho các tập phim:

```bash
php artisan vsphim:episode:change_domain_play
```

### Cấu hình

#### Môi trường Production

Cập nhật file `.env`:

```env
APP_NAME="Tên Ứng Dụng"
APP_ENV=production
APP_DEBUG=false
APP_URL=https://your-domain.com
```

#### Múi giờ và Ngôn ngữ

Trong `config/app.php`:

```php
'timezone' => 'Asia/Ho_Chi_Minh',
'locale' => 'vi',
```

### Tác vụ theo lịch

Để tự động reset lượt xem, thêm vào crontab:

```bash
* * * * * cd /path/to/project && php artisan schedule:run >> /dev/null 2>&1
```

Tác vụ này sẽ:
- Reset lượt xem ngày vào nửa đêm
- Reset lượt xem tuần theo tuần
- Reset lượt xem tháng theo tháng

### Tài nguyên

- **Trang chủ**: [Vsphim.com](https://vsphim.com)
- **Add-ons**: [Vsphim Crawler](https://github.com/vsphim/vsphim-crawler)
- **Giao diện**: [Thêm giao diện...](https://vsphim.com)

### Hỗ trợ

Để báo lỗi, đặt câu hỏi hoặc đóng góp, vui lòng truy cập [GitHub repository](https://github.com/vsphim/vsphim-core).

### Giấy phép

Package này là phần mềm mã nguồn mở được cấp phép theo [MIT license](LICENSE.md).

---

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for more information.

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## Security

If you discover any security-related issues, please email vsphim@vsphim.com instead of using the issue tracker.
