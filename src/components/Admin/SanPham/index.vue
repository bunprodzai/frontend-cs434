<template>
    <div class="container-fluid">
        <div class="row mb-2">
            <div class="col-lg-12 text-end">
                <button class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#addModal"><i
                        class="fa-solid fa-square-plus"></i>Thêm Mới Sản Phẩm</button>
            </div>
        </div>
        <div class="row">
            <div class="col-lg-12">
                <div class="card">
                    <div class="card-header">
                        <h4>Danh Sách Sản Phẩm</h4>
                    </div>
                    <div class="card-body">
                        <div class="table-responsive">
                            <table class="table table-bordered table-hover">
                                <thead class="text-center table-success">
                                    <tr>
                                        <th>#</th>
                                        <th>Tên Sản Phẩm</th>
                                        <th>Hình Ảnh</th>
                                        <th>Mô Tả</th>
                                        <th>Giá Bán</th>
                                        <th>Tình Trạng</th>
                                        <th>Số Lượng Tồn</th>
                                        <th>% Giảm Giá</th>
                                        <th>Action</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <template v-for="(value, index) in clothes" :key="index">
                                        <tr>
                                            <th class="align-middle text-center">{{ index + 1 }}</th>
                                            <td class="align-middle">{{ value.ten_san_pham }}</td>
                                            <td>
                                                <img v-bind:src="value.hinh_anh" class="img-fluid"
                                                    style="width: 70px; height: 120px;" :alt="value.alt">
                                            </td>
                                            <td class="align-middle">{{ value.mo_ta }}
                                            </td>
                                            <td class="align-middle text-end">{{ formatVND(value.gia_ban) }}</td>
                                            <td class="align-middle text-center">
                                                <span v-if="value.tinh_trang == 1" class="badge bg-success">Còn
                                                    Hàng</span>
                                                <span v-else class="badge bg-warning text-dark">Hết Hàng</span>
                                            </td>
                                            <td class="align-middle text-center">{{ value.so_luong_ton }}</td>
                                            <td class="align-middle text-center">{{ value.giam_gia }} %</td>
                                            <td class="align-middle text-center">
                                                <button class="btn btn-primary me-2" data-bs-toggle="modal"
                                                    data-bs-target="#editModal">Chỉnh Sửa</button>
                                                <button class="btn btn-danger" data-bs-toggle="modal"
                                                    data-bs-target="#delModal">Xóa</button>
                                            </td>
                                        </tr>
                                    </template>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal Thêm Mới -->
    <div class="modal fade" id="addModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-lg">
            <div class="modal-content">
                <div class="modal-header">
                    <h1 class="modal-title fs-5" id="exampleModalLabel">Thêm Mới Sản Phẩm</h1>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    ...
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Đóng</button>
                    <button type="button" class="btn btn-primary" data-bs-dismiss="modal">Thêm</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal Chỉnh Sửa -->
    <div class="modal fade" id="editModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog modal-lg">
            <div class="modal-content">
                <div class="modal-header">
                    <h1 class="modal-title fs-5" id="exampleModalLabel">Cập Nhật Sản Phẩm</h1>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    ...
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Đóng</button>
                    <button type="button" class="btn btn-primary" data-bs-dismiss="modal">Lưu</button>
                </div>
            </div>
        </div>
    </div>
    <!-- Modal Xóa -->
    <div class="modal fade" id="delModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h1 class="modal-title fs-5" id="exampleModalLabel">Thông Báo!</h1>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    ...
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Đóng</button>
                    <button type="button" class="btn btn-danger" data-bs-dismiss="modal">Xác Nhận</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            clothes: [
                {
                    id: 1,
                    ten_san_pham: "Áo Thun Nam Basic",
                    mo_ta: "Áo thun cotton co giãn, thoáng mát.",
                    gia_ban: 99000,
                    tinh_trang: 1,
                    so_luong_ton: 25,
                    giam_gia: 5,
                    hinh_anh: "https://down-vn.img.susercontent.com/file/sg-11134201-7rbk2-lqk3v5k7v7kqf2",
                    alt: "Áo Thun Nam Basic"
                },
                {
                    id: 2,
                    ten_san_pham: "Quần Jean Nữ Skinny",
                    mo_ta: "Quần jean ôm dáng, co giãn nhẹ.",
                    gia_ban: 199000,
                    tinh_trang: 1,
                    so_luong_ton: 12,
                    giam_gia: 10,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Quần Jean Nữ Skinny"

                },
                {
                    id: 3,
                    ten_san_pham: "Áo Sơ Mi Trắng Nam",
                    mo_ta: "Áo sơ mi vải cotton, cổ bẻ.",
                    gia_ban: 159000,
                    tinh_trang: 1,
                    so_luong_ton: 18,
                    giam_gia: 0,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Quần Jean Nữ Skinny"
                },
                {
                    id: 4,
                    ten_san_pham: "Váy Xòe Nữ",
                    mo_ta: "Váy xòe chất liệu voan nhẹ nhàng.",
                    gia_ban: 220000,
                    tinh_trang: 1,
                    so_luong_ton: 10,
                    giam_gia: 15,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Váy Xòe Nữ"
                },
                {
                    id: 5,
                    ten_san_pham: "Áo Khoác Gió Nam",
                    mo_ta: "Áo khoác chống nước, nhẹ, dễ mặc.",
                    gia_ban: 250000,
                    tinh_trang: 1,
                    so_luong_ton: 8,
                    giam_gia: 20,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Áo Khoác Gió Nam"
                },
                {
                    id: 6,
                    ten_san_pham: "Quần Short Nữ",
                    mo_ta: "Quần short kaki, thoải mái cho mùa hè.",
                    gia_ban: 89000,
                    tinh_trang: 1,
                    so_luong_ton: 30,
                    giam_gia: 0,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Quần Short Nữ"
                },
                {
                    id: 7,
                    ten_san_pham: "Áo Polo Nam",
                    mo_ta: "Áo polo cổ bẻ, chất liệu cotton.",
                    gia_ban: 129000,
                    tinh_trang: 1,
                    so_luong_ton: 22,
                    giam_gia: 7,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Áo Polo Nam"
                },
                {
                    id: 8,
                    ten_san_pham: "Quần Tây Nam",
                    mo_ta: "Quần tây vải mềm, lịch sự.",
                    gia_ban: 180000,
                    tinh_trang: 1,
                    so_luong_ton: 15,
                    giam_gia: 0,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Quần Tây Nam"
                },
                {
                    id: 9,
                    ten_san_pham: "Áo Khoác Jean Nữ",
                    mo_ta: "Áo khoác jean cá tính, trẻ trung.",
                    gia_ban: 270000,
                    tinh_trang: 1,
                    so_luong_ton: 7,
                    giam_gia: 12,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Áo Khoác Jean Nữ"
                },
                {
                    id: 10,
                    ten_san_pham: "Váy Bodycon Nữ",
                    mo_ta: "Váy bodycon ôm sát, tôn dáng.",
                    gia_ban: 210000,
                    tinh_trang: 1,
                    so_luong_ton: 9,
                    giam_gia: 8,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Váy Bodycon Nữ"
                },
                {
                    id: 11,
                    ten_san_pham: "Áo Hoodie Nam",
                    mo_ta: "Áo hoodie nỉ, giữ ấm tốt.",
                    gia_ban: 190000,
                    tinh_trang: 1,
                    so_luong_ton: 14,
                    giam_gia: 10,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Áo Hoodie Nam"
                },
                {
                    id: 12,
                    ten_san_pham: "Quần Jogger Nữ",
                    mo_ta: "Quần jogger thể thao, năng động.",
                    gia_ban: 120000,
                    tinh_trang: 1,
                    so_luong_ton: 20,
                    giam_gia: 5,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Quần Jogger Nữ"
                },
                {
                    id: 13,
                    ten_san_pham: "Áo Len Nam",
                    mo_ta: "Áo len cổ tròn, giữ ấm mùa đông.",
                    gia_ban: 160000,
                    tinh_trang: 0,
                    so_luong_ton: 11,
                    giam_gia: 0,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Áo Len Nam"
                },
                {
                    id: 14,
                    ten_san_pham: "Váy Maxi Nữ",
                    mo_ta: "Váy maxi dài, chất liệu voan.",
                    gia_ban: 230000,
                    tinh_trang: 0,
                    so_luong_ton: 6,
                    giam_gia: 18,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Váy Maxi Nữ"
                },
                {
                    id: 15,
                    ten_san_pham: "Áo Thun Trơn Nữ",
                    mo_ta: "Áo thun trơn, nhiều màu sắc.",
                    gia_ban: 85000,
                    tinh_trang: 1,
                    so_luong_ton: 28,
                    giam_gia: 0,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Áo Thun Trơn Nữ"
                },
                {
                    id: 16,
                    ten_san_pham: "Quần Legging Nữ",
                    mo_ta: "Quần legging co giãn, ôm sát.",
                    gia_ban: 95000,
                    tinh_trang: 0,
                    so_luong_ton: 19,
                    giam_gia: 6,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Quần Legging Nữ"
                },
                {
                    id: 17,
                    ten_san_pham: "Áo Khoác Dù Nam",
                    mo_ta: "Áo khoác dù nhẹ, chống gió.",
                    gia_ban: 210000,
                    tinh_trang: 1,
                    so_luong_ton: 13,
                    giam_gia: 9,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Áo Khoác Dù Nam"
                },
                {
                    id: 18,
                    ten_san_pham: "Quần Baggy Nữ",
                    mo_ta: "Quần baggy vải mềm, thoải mái.",
                    gia_ban: 140000,
                    tinh_trang: 1,
                    so_luong_ton: 17,
                    giam_gia: 0,
                    hinh_anh: "https://cf.shopee.vn/file/7c6e2e4f0e2e2b2b5e7b6e7b6e7b6e7b",
                    alt: "Quần Baggy Nữ"
                },
                {
                    id: 19,
                    ten_san_pham: "Áo Sơ Mi Kẻ Nam",
                    mo_ta: "Áo sơ mi kẻ sọc, trẻ trung.",
                    gia_ban: 155000,
                    tinh_trang: 1,
                    so_luong_ton: 16,
                    giam_gia: 4,
                    hinh_anh: "https://cf.shopee.vn/file/sg-11134201-7rbk2-lqk3v5k7v7kqfi",
                    alt: "Áo Sơ Mi Kẻ Nam"
                },
                {
                    id: 20,
                    ten_san_pham: "Váy Suông Nữ",
                    mo_ta: "Váy suông đơn giản, dễ mặc.",
                    gia_ban: 175000,
                    tinh_trang: 0,
                    so_luong_ton: 12,
                    giam_gia: 11,
                    hinh_anh: "https://cf.shopee.vn/file/sg-11134201-7rbk2-lqk3v5k7v7kqfj",
                    alt: "Váy Suông Nữ"
                }
            ]
        }
    },
    methods: {
        formatVND(amount) {
            return new Intl.NumberFormat('vi-VN', { style: 'currency', currency: 'VND', }).format(amount);
        }
    },
}
</script>
<style></style>