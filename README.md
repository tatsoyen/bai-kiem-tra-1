# Ứng dụng Kiểm tra Số dư Token ERC20 trên Ronin Saigon

Đây là một dự án TypeScript đơn giản giúp kiểm tra số dư của một Token ERC20 trên mạng Ronin Saigon (một blockchain tương thích EVM). Dự án này được thiết kế cho học sinh từ lớp 9 đến lớp 12 để học cách tương tác với blockchain.

## Giới thiệu

Ứng dụng này cho phép bạn:
- Kết nối đến mạng Ronin Saigon
- Tương tác với hợp đồng thông minh ERC20
- Kiểm tra số dư token của một địa chỉ ví

## Yêu cầu hệ thống

- Node.js (phiên bản 14 trở lên)
- npm hoặc yarn

## Hướng dẫn cài đặt

### Bước 1: Cài đặt Node.js và npm

1. Tải và cài đặt Node.js từ [trang chủ Node.js](https://nodejs.org/)
2. Kiểm tra cài đặt bằng cách mở Terminal (hoặc Command Prompt trên Windows) và gõ:
   ```
   node --version
   npm --version
   ```

### Bước 2: Cài đặt các thư viện cần thiết

1. Mở Terminal (hoặc Command Prompt) và di chuyển đến thư mục dự án:
   ```
   cd đường-dẫn-đến-thư-mục-dự-án
   ```

2. Cài đặt các thư viện cần thiết:
   ```
   npm install
   ```

## Hướng dẫn sử dụng

### Bước 1: Chạy ứng dụng

1. Trong thư mục dự án, chạy lệnh:
   ```
   npm start
   ```

2. Ứng dụng sẽ kết nối đến mạng Ronin Saigon và hiển thị thông tin kết nối.

### Bước 2: Nhập thông tin

1. Nhập địa chỉ hợp đồng Token ERC20 (bắt đầu bằng 0x) khi được yêu cầu.
   - Ví dụ: `0x1A2B3C4D5E6F7G8H9I0J1K2L3M4N5O6P7Q8R9S0`

2. Nhập địa chỉ ví cần kiểm tra số dư (bắt đầu bằng 0x) khi được yêu cầu.
   - Ví dụ: `0xA1B2C3D4E5F6G7H8I9J0K1L2M3N4O5P6Q7R8S9`

### Bước 3: Xem kết quả

Ứng dụng sẽ hiển thị:
- Thông tin về Token (tên, ký hiệu, số thập phân)
- Số dư của địa chỉ ví đã nhập

## Giải thích mã nguồn

### 1. Kết nối đến blockchain

Chúng ta sử dụng thư viện `ethers.js` để kết nối đến mạng Ronin Saigon thông qua một điểm truy cập RPC (Remote Procedure Call):

```typescript
const provider = new ethers.providers.JsonRpcProvider(config.roninSaigonRPC);
```

### 2. Tương tác với hợp đồng thông minh

Chúng ta tạo một đối tượng hợp đồng để tương tác với token ERC20:

```typescript
const tokenContract = new ethers.Contract(tokenAddress, erc20ABI, provider);
```

### 3. Kiểm tra số dư

Chúng ta gọi hàm `balanceOf` của hợp đồng ERC20 để lấy số dư của một địa chỉ:

```typescript
const balance = await tokenContract.balanceOf(walletAddress);
```

### 4. Hiển thị kết quả

Chúng ta chuyển đổi số dư từ dạng "raw" (số nguyên lớn) sang dạng dễ đọc bằng cách tính đến số thập phân của token:

```typescript
const readableBalance = ethers.utils.formatUnits(balance, decimals);
```

## Mở rộng dự án

Bạn có thể mở rộng dự án này bằng cách:
1. Thêm giao diện người dùng đồ họa (GUI)
2. Lưu lịch sử kiểm tra số dư
3. Thêm chức năng chuyển token
4. Hiển thị giá trị token theo đơn vị tiền tệ (USD, VND...)

## Tìm hiểu thêm

- [Tài liệu về ethers.js](https://docs.ethers.io/)
- [Tiêu chuẩn ERC20](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/)
- [Ronin Blockchain](https://roninchain.com/)