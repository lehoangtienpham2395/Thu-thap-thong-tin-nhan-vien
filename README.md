<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Thu Thập Thông Tin</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 20px;
            max-width: 600px;
            margin: auto;
        }
        h2 {
            text-align: center;
        }
        form {
            display: flex;
            flex-direction: column;
        }
        label, input, button {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <h2>Thu Thập Thông Tin</h2>
    <p>Xin chào, bạn vui lòng nhập đầy đủ thông tin dưới đây nhé. Lưu ý, phải nhập đúng các thông tin dưới đây, nó sẽ giúp cho phần hoàn tất hồ sơ của bạn được nhanh hơn và có thể đi làm sớm nhất.</p>
    <form id="dataForm">
        <label for="fullName">Họ tên đầy đủ:</label>
        <input type="text" id="fullName" name="fullName" required>
        
        <label for="phoneNumber">Số điện thoại:</label>
        <input type="tel" id="phoneNumber" name="phoneNumber" required>
        
        <label for="hanhKiem">Giấy xác nhận hạnh kiểm:</label>
        <input type="file" id="hanhKiem" name="hanhKiem" accept="image/*" required>
        
        <label for="cccdFront">CCCD mặt trước:</label>
        <input type="file" id="cccdFront" name="cccdFront" accept="image/*" required>
        
        <label for="cccdBack">CCCD mặt sau:</label>
        <input type="file" id="cccdBack" name="cccdBack" accept="image/*" required>
        
        <button type="submit">Gửi thông tin</button>
    </form>
</body>
</html>
