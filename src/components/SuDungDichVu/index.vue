<template>
    <div class="row">
        <div class="col-12">
            <div class="card">
                <div class="card-body">
                    <!-- <ul class="nav nav-tabs nav-primary" role="tablist">
                    <template v-for="(v, k) in list_khu_vuc">
                        <li class="nav-item" role="presentation">
                            <a class="nav-link" data-bs-toggle="tab" role="tab" aria-selected="false">
                                <div class="d-flex align-items-center">
                                    <div class="tab-icon me-1 text-danger fa-2x">
                                        <span v-html="v.icon"></span>
                                    </div>
                                    <div class="tab-title">{{ v.ten_khu }}</div>
                                </div>
                            </a>
                        </li>
                    </template>
                </ul> -->
                    <div class="tab-content py-3">
                        <div class="row">
                            <template v-for="(v, k) in list_ban">
                                <div class="col-2">
                                    <div class="tab-pane fade show" id="primaryhome" role="tabpanel">
                                        <div class="card radius-10">
                                            <div class="card-body">
                                                <div class="text-center">
                                                    <div
                                                        class="widgets-icons rounded-circle mx-auto bg-light-primary text-primary mb-3">
                                                        <i class="fa-solid fa-couch"></i>
                                                    </div>
                                                    <h4 class="my-1">{{ v.ten_ban }}</h4>
                                                    <button 
                                                        v-if="v.is_mo_ban == 0" class="btn btn-primary"
                                                        v-on:click="MoBan(v)" data-bs-toggle="modal" data-bs-target="#mobanModal">Mở Bàn</button>
                                                    <button data-bs-toggle="modal" data-bs-target="#mobanModal" v-else class="btn btn-success">Thanh
                                                        Toán</button>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </template>
                        </div>
                        <div class="modal fade" id="mobanModal" tabindex="-1" aria-labelledby="exampleModalLabel"
                        aria-hidden="true">
                        <div class="modal-dialog modal-xl" style="max-width: 100%;">
                            <div class="modal-content">
                                <div class="modal-header">
                                    <h1 class="modal-title fs-5" id="exampleModalLabel">Mở Bàn</h1>
                                    <button type="button" class="btn-close" data-bs-dismiss="modal"
                                        aria-label="Close"></button>
                                </div>
                                <div class="modal-body">
                                    <div class="row">
                                        <div class="col-md-4">
                                            <div class="card">
                                                <div class="card-header">
                                                    <h6>Danh sách món ăn</h6>
                                                </div>
                                                <div class="card-body">
                                                    <div class="mb-3">
                                                        <div class="table-responsive" style="max-height: 450px">
                                                            <table class="table table-bordered">
                                                                <thead>
                                                                    <tr>
                                                                        <th class="align-middle text-center">#</th>
                                                                        <th class="align-middle text-center">Tên Hàng</th>
                                                                        <th class="align-middle text-center">Action</th>
                                                                    </tr>
                                                                </thead>
                                                                <tbody>
                                                                    <template v-for="(value, key) in list_mon_an">
                                                                        <tr>
                                                                            <td class="align-middle text-center">{{ key + 1
                                                                            }}</td>
                                                                            <td class="align-middle text-center">{{
                                                                                value.ten_mon }}</td>
                                                                            <td class="align-middle text-center">
                                                                                <button v-on:click="themMonAn(value)"
                                                                                    class="btn btn-primary">Thêm</button>
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
                                        <div class="col-md-8">
                                            <div class="card">
                                                <div class="card-header">
                                                    Món ăn sử dụng
                                                </div>
                                                <div class="card-body">
                                                    <table class="table table-bordered">
                                                        <thead>
                                                            <tr>
                                                                <th class="text-center align-middle">#</th>
                                                                <th class="text-center align-middle">Tên món ăn</th>
                                                                <th class="text-center align-middle">Số lượng</th>
                                                                <th class="text-center align-middle">Đơn giá</th>
                                                                <th class="text-center align-middle">% giảm giá</th>
                                                                <th class="text-center align-middle">Thành tiền</th>
                                                                <th class="text-center align-middle">Ghi chú</th>
                                                                <th class="text-center align-middle">Action</th>
                                                            </tr>
                                                        </thead>
                                                        <tbody>
                                                            <!-- <template v-for="(v, k) in list_chi_tiet_ban_hang">
                                                                <tr>
                                                                    <th class="align-middle">{{ k + 1 }}</th>
                                                                    <td class="align-middle">{{ v.ten_mon }}</td>
                                                                    <td class="align-middle">
                                                                        <input v-on:change="updateChiTiet(v)" type="number"
                                                                            class="form-control" v-model="v.so_luong">
                                                                    </td>
                                                                    <td class="align-middle">
                                                                        <input v-on:change="updateChiTiet(v)" type="number"
                                                                            class="form-control" v-model="v.don_gia">
                                                                    </td>
                                                                    <td class="align-middle">
                                                                        <input v-on:change="updateChiTiet(v)" type="number"
                                                                            class="form-control" v-model="v.phan_tram_giam">
                                                                    </td>
                                                                    <td class="align-middle">{{ v.thanh_tien }}</td>
                                                                    <td class="align-middle">
                                                                        <input v-on:change="updateChiTiet(v)" type="text"
                                                                            class="form-control" v-model="v.ghi_chu">
                                                                    </td>
                                                                    <td class="align-middle">
                                                                        <button class="btn btn-danger">Xóa</button>
                                                                    </td>
                                                                </tr>
                                                            </template> -->
                                                        </tbody>
                                                    </table>
                                                </div>
                                                <div class="card-footer bg-white text-end">
                                                    <div class="row">
                                                        <div class="col-7">
                                                            <textarea v-model="ghi_chu_hoa_don" class="form-control"
                                                                cols="30" rows="4"></textarea>
                                                        </div>
                                                        <div class="col-5">
                                                            <div class="row">
                                                                <div class="col-6">
                                                                    <p><b>Tổng thanh toán:</b></p>
                                                                    <p class="mt-3"><b>Phần trăm giảm: </b></p>
                                                                    <p><b>Tiền thực thu: </b></p>
                                                                </div>
                                                                <!-- <div class="col-6">
                                                                    <p><b>{{ tong_tien }} đ</b></p>
                                                                    <input type="number" class="form-control"
                                                                        v-on:change="updateHoaDon()"
                                                                        v-model="phan_tram_giam_hoa_don">
                                                                    <p class="mt-3"><b>{{ tien_thuc_thu }} đ</b>
                                                                    </p>
                                                                </div> -->
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                                <div class="modal-footer">
                                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Đóng</button>
                                    <button type="button" class="btn btn-primary" data-bs-dismiss="modal"
                                        >Thanh Toán</button>
                                </div>
                            </div>
                        </div>
                    </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios';
import baseRequest from '../../core/baseRequest';
import { createToaster } from "@meforma/vue-toaster";
const toaster = createToaster({ position: "top-right" });
export default {
    data() {
        return {
            list_khu_vuc: [],
            list_ban: [],
            list_mon_an : []
        }
    },
    mounted() {
        this.loadDataKhuVuc();
        this.loadDataBan();
        this.loadMonAn();
    },
    methods: {
        loadDataKhuVuc() {
            axios
                .get('http://127.0.0.1:8000/api/admin/khu-vuc/lay-du-lieu-hoat-dong')
                .then((res) => {
                    this.list_khu_vuc = res.data.khu_vuc;
                });
        },

        loadDataBan() {
            axios
                .get('http://127.0.0.1:8000/api/admin/ban/lay-du-lieu')
                .then((res) => {
                    this.list_ban = res.data.ban;
                });
        },

        MoBan(v) {
            axios
                .post('http://127.0.0.1:8000/api/admin/hoa-don-dich-vu/mo-ban', v)
                .then((res) => {
                    if (res.data.status) {
                        toaster.success(res.data.message);
                        this.loadDataBan();
                    }
                });
        },
        loadMonAn() {
            axios
                .get('http://127.0.0.1:8000/api/admin/hoa-don-dich-vu/lay-du-lieu-mon-an')
                .then((res) => {
                    this.list_mon_an = res.data.data;
                });
        },
    }
}
</script>
<style></style>