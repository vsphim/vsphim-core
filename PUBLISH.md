# Hướng dẫn Publish Package lên Packagist

## Bước 1: Chuẩn bị Repository

1. Đảm bảo code đã được push lên Git repository (GitHub, GitLab, hoặc Bitbucket)
2. Repository phải là **public** hoặc bạn có quyền truy cập
3. Repository URL ví dụ: `https://github.com/vsphim/vsphim-core`

## Bước 2: Thêm Repository vào composer.json (Tùy chọn)

Nếu muốn, bạn có thể thêm repository vào `composer.json`:

```json
{
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/vsphim/vsphim-core"
        }
    ]
}
```

**Lưu ý**: Bạn có thể bỏ qua bước này vì Packagist sẽ tự động detect repository khi bạn submit.

## Bước 3: Tạo Git Tags cho Version

Packagist sử dụng Git tags để xác định version. Tạo tag cho version đầu tiên:

```bash
git tag -a v1.0.0 -m "First release"
git push origin v1.0.0
```

Hoặc sử dụng semantic versioning:
- `v1.0.0` - Major release
- `v1.0.1` - Patch release  
- `v1.1.0` - Minor release

## Bước 4: Validate composer.json

Chạy lệnh để kiểm tra:

```bash
composer validate
```

Đảm bảo không có lỗi, chỉ có warnings (nếu có).

## Bước 5: Đăng ký và Submit lên Packagist

1. Truy cập https://packagist.org/
2. Đăng ký tài khoản hoặc đăng nhập (có thể dùng GitHub login)
3. Click vào **Submit** trong menu
4. Nhập repository URL của bạn (ví dụ: `https://github.com/vsphim/vsphim-core`)
5. Click **Check** để Packagist kiểm tra
6. Nếu thành công, click **Submit** để publish

## Bước 6: Kiểm tra Package

Sau khi submit, Packagist sẽ:
- Tự động crawl repository
- Tạo package page tại: `https://packagist.org/packages/vsphim/vsphim-core`
- Cập nhật tự động khi bạn push tags mới

## Bước 7: Cài đặt Package

Sau khi publish, người khác có thể cài đặt bằng:

```bash
composer require vsphim/vsphim-core
```

## Lưu ý quan trọng

1. **Dependencies**: Đảm bảo tất cả dependencies trong `composer.json` đều có sẵn trên Packagist
2. **Version Tags**: Luôn tạo Git tags cho mỗi version mới
3. **README.md**: Nên có README.md trong repository để hiển thị trên Packagist
4. **License**: Đảm bảo có file LICENSE nếu sử dụng license khác MIT
5. **Stability**: Package phải có `"minimum-stability": "stable"` hoặc tags phải có format đúng

## Troubleshooting

### Lỗi: "Package not found"
- Kiểm tra repository URL đúng chưa
- Đảm bảo repository là public
- Kiểm tra `composer.json` có đúng format

### Lỗi: "Dependency not found"
- Kiểm tra tất cả dependencies trong `require` đều có trên Packagist
- Nếu dependency là private, cần thêm vào `repositories`

### Package không tự động update
- Đảm bảo đã tạo Git tags
- Kiểm tra webhook trong Packagist settings (nếu có)
- Có thể click "Update" thủ công trên Packagist

## Tài liệu tham khảo

- [Packagist Documentation](https://packagist.org/)
- [Composer Documentation](https://getcomposer.org/doc/)
- [Semantic Versioning](https://semver.org/)

