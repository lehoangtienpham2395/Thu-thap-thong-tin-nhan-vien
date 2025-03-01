<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form Thu Thập Thông Tin</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 20px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 800px;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            margin: auto;
        }
        h2 {
            text-align: center;
            color: #004d40;
        }
        .highlight {
            background-color: #ffeb3b;
            padding: 10px;
            border-radius: 5px;
            font-weight: bold;
            color: #d32f2f;
            text-align: center;
            margin-bottom: 15px;
        }
        .form-group {
            display: flex;
            flex-wrap: wrap;
            margin-bottom: 15px;
        }
        .form-group label {
            width: 30%;
            padding: 10px;
            font-weight: bold;
        }
        .form-group input {
            width: 65%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .form-group input[type="file"] {
            border: none;
        }
        .button-group {
            text-align: center;
            margin-top: 20px;
        }
        button {
            background-color: #004d40;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #00332e;
        }
    </style>
</head>
<body>

<div class="container">
    <p class="highlight">
        Lưu ý, nhập đúng và đầy đủ các thông tin dưới đây, nó sẽ giúp cho phần hoàn tất hồ sơ của bạn được nhanh hơn và có thể đi làm sớm nhất có thể. Cảm ơn sự hợp tác của bạn!
    </p>

    <form id="dataForm">
        <div class="form-group">
            <label for="fullName">Họ tên đầy đủ:</label>
            <input type="text" id="fullName" name="fullName" required>
        </div>
        
        <div class="form-group">
            <label for="phoneNumber">Số điện thoại:</label>
            <input type="tel" id="phoneNumber" name="phoneNumber" required>
        </div>
        
        <div class="form-group">
            <label for="hanhKiem">Giấy xác nhận hạnh kiểm:</label>
            <input type="file" id="hanhKiem" name="hanhKiem" accept="image/*">
        </div>
        
        <div class="form-group">
            <label for="cccdFront">CCCD mặt trước:</label>
            <input type="file" id="cccdFront" name="cccdFront" accept="image/*" required>
        </div>
        
        <div class="form-group">
            <label for="cccdBack">CCCD mặt sau:</label>
            <input type="file" id="cccdBack" name="cccdBack" accept="image/*" required>
        </div>

        <div class="button-group">
            <button type="submit">Gửi thông tin</button>
        </div>
    </form>
</div>

<script>
document.getElementById("dataForm").addEventListener("submit", function(event) {
    event.preventDefault();

    let formData = new FormData();
    formData.append("fullName", document.getElementById("fullName").value);
    formData.append("phoneNumber", document.getElementById("phoneNumber").value);
    formData.append("hanhKiem", document.getElementById("hanhKiem").files[0]);
    formData.append("cccdFront", document.getElementById("cccdFront").files[0]);
    formData.append("cccdBack", document.getElementById("cccdBack").files[0]);

    fetch("https://script.google.com/macros/s/AKfycbyV7jGT-EOssEqkb_l0DkbdrVLckQofDgOGUFqjiNAIIT-1Qtj_hUi5W66Q2c-kx7Ks/exec", {
        method: "POST",
        body: formData
    })
    .then(response => response.json())
    .then(data => {
        if (data.status === "success") {
            alert("Dữ liệu đã được gửi thành công! Link thư mục: " + data.folderUrl);
        } else {
            alert("Có lỗi xảy ra: " + data.message);
        }
    })
    .catch(error => {
        console.error("Lỗi:", error);
        alert("Có lỗi xảy ra! Hãy thử lại.");
    });
});

</script>

</body>
</html>

