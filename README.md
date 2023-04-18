# Base-Node

Trải nghiệm chạy Node dự án Base, cấu hình dự án khuyến cáo như dưới đây:

    4 Core CPU
    8Gb Ram
    100GB SSD
    
    Cần 1 tài khoản Alchemy free. Đăng kí tại đây: https://dashboard.alchemy.com/
    VPS của Digital Ocean, chi phí 5$ tặng 200$ cho người mới tham gia lần đầu: https://bit.ly/DigitalOcean200 
    Video hướng dẫn: https://youtu.be/IdofxspCOQk
    
1/ Login vào VPS sau khi khởi tạo: dùng Terminal (MACOS), hoặc Mobaxterm, SSH login... (Windown)

    ssh root@<địa chỉ IP VPS>
    
    "Nhập mật khẩu VPS, lưu ý là sẽ không hiện"
    
2/ Cập nhật và nâng cấp VPS:

    sudo apt update && apt upgrade -y
    
3/ Cài đặt Docker Engine:

    sudo apt-get update
    sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release

Copy & Paste

    sudo mkdir -m 0755 -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

Copy & Paste

    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

Copy & Paste

    sudo apt-get update -y

    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
    
4/ Tải về bộ github của dự án Base:

    git clone https://github.com/base-org/node.git
    cd node
    
Sửa thông tin file Docker-compose.yaml :

    nano docker-compose.yml

lưu ý đoạn này cần kiểm tra kỹ dòng:

    - OP_NODE_L1_ETH_RPC=https://eth-goerli.g.alchemy.com/xxxxxxxxxxxxxxxxxxx
    
Lấy link này bằng cách mở Alchemy đã tạo free ở trên => Create App => Đặt tên tuỳ ý, chọn như dưới đây:
 
    Chain: Ethereum
    Network: Ethereum Goerli
    Creat App
    
Nhấn Viewkey, chọn dòng thứ 2 có đường LINK của bạn, thay thế cho dòng https://eth-goerli.g.alchemy.com/xxxxxxxxxxxxxxxxxxx

Nhập lệnh để lưu lại:

    control O

Gõ enter

    control X
    
5/ Chạy node Base:

    docker compose up -d
    
    curl -d '{"id":0,"jsonrpc":"2.0","method":"eth_getBlockByNumber","params":["latest",false]}' \
    -H "Content-Type: application/json" http://localhost:8545

check logs:

    docker compose logs -f
    
    
Cộng đồng chạy Node & Validator VietNam, nơi thảo luận và chia sẻ kinh nghiệm về chạy node/validator.

    Chanel: https://t.me/RunnodeVietNamese
    Youtube: https://www.youtube.com/@nodevalidatorvietnam
    Twitter: https://twitter.com/NodeValidatorVN

    
