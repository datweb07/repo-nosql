**Cách setup đọc secret key:**

1. Click vào biểu tượng **khóa** ở thanh menu bên trái giao diện Colab (Khóa bí mật).
2. Nhấn vào nút **Thêm giá trị bí mật mới**.
3. Phần **Tên**: Nhập `MONGODB_URI`.
4. Phần **Giá trị**: Dán chuỗi kết nối MongoDB Atlas vào đây.
5. Bật công tắc **Quyền truy cập vào sổ tay** ở bên cạnh cái key .

**Sau đó, sử dụng đoạn code Python dưới đây để kết nối:**

```python
from pymongo.mongo_client import MongoClient
from pymongo.server_api import ServerApi
from google.colab import userdata

uri = userdata.get('MONGODB_URI')

client = MongoClient(uri, server_api=ServerApi('1'))

try:
    client.admin.command('ping')
    print("Kết nối MongoDB thành công!")
except Exception as e:
    print(e)
```
