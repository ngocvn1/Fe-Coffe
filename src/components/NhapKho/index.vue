<template lang="">
<div class="row">
    <div class="col-5">
        <div class="card">
            <div class="card-header">
                Danh Sách Nguyên Liệu
            </div>
            <div class="card-body">
                <div class="table-responsive">
                    <table class="table table-bordered">
                        <thead>
                            <tr>
                                <th colspan="100%">
                                    <div class="input-group mb-3">
                                        <input v-on:keyup.enter="searchNguyenLieu()" v-model="key_search.abc" type="text" class="form-control" placeholder="Nhập thông tin cần tìm">
                                        <button class="btn btn-primary" v-on:click="searchNguyenLieu()">
                                            <i class="fa-solid fa-magnifying-glass"></i>
                                        </button>
                                    </div>
                                </th>
                            </tr>
                            <tr>
                                <th class="text-center align-middle text-nowrap">#</th>
                                <th class="text-center align-middle text-nowrap">Tên Nguyên Liệu</th>
                                <th class="text-center align-middle text-nowrap">Action</th>
                            </tr>
                        </thead>
                        <tbody>
                            <template v-for="(value, key) in list_nguyen_lieu">
                                <tr>
                                    <th class="text-center align-middle text-nowrap">{{key + 1}}</th>
                                    <td class="align-middle text-nowrap">{{value.ten_nguyen_lieu}}</td>
                                    <th class="text-center align-middle text-nowrap">
                                        <button class="btn btn-primary" v-on:click="addnguyenLieu(value)">Thêm</button>
                                    </th>
                                </tr>
                            </template>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
    <div class="col-7">
        <div class="card">
            <div class="card-header">
                Danh Sách Nhập Kho
            </div>
            <div class="card-body">
                <div class="table-responsive">
                    <table class="table table-bordered">
                        <thead>
                            <tr>
                                <th class="text-center align-middle text-nowrap">#</th>
                                <th class="text-center align-middle text-nowrap">Tên Nguyên Liệu</th>
                                <th class="text-center align-middle text-nowrap">Số Lương</th>
                                <th class="text-center align-middle text-nowrap">Đơn Giá</th>
                                <th class="text-center align-middle text-nowrap">Thành Tiền</th>
                                <th class="text-center align-middle text-nowrap">Action</th>
                            </tr>
                        </thead>
                        <tbody>
                            <template v-for="(value, key) in list_nhap_kho">
                                <tr>
                                    <th class="text-center align-middle text-nowrap">{{key + 1}}</th>
                                    <td class="align-middle text-nowrap">{{value.ten_nguyen_lieu}}</td>
                                    <td class="text-center align-middle text-nowrap">
                                        <input type="text" v-model="value.so_luong" v-on:change="updateNhapKho(value)" class="form-control">
                                    </td>
                                    <td class="text-center align-middle text-nowrap">
                                        <input type="text" v-model="value.don_gia" v-on:change="updateNhapKho(value)" class="form-control">
                                    </td>
                                    <td class="text-center align-middle text-nowrap">{{value.thanh_tien}}</td>
                                    <td class="text-center align-middle text-nowrap">
                                        <i class="fa-solid fa-trash fa-2x text-danger" v-on:click="deletenguyenLieu(value)"></i>
                                    </td>
                                </tr>
                            </template>
                                <tr>
                                    <td colspan="5">
                                        
                                        <label for="" class="mb-2">Chọn Nhà Cung Cấp</label>
                                        <select name="" class="form-control" id="">
                                            <option value=""></option>
                                        </select>
                                    </td>
                                    <td colspan="1">
                                        <label for="" class="mb-2">Tổng Tiền</label>
                                        <span class="text-danger"></span>
                                    </td>
                                    <td colspan="2" class="text-center align-middle text-nowrap">
                                        
                                    </td>
                                </tr>
                        </tbody>
                    </table>
                </div>
                <div class="row">
                    <div class="col-lg-12">
                        <button class="btn btn-primary" style="" >Nhập Kho</button>
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
            list_nguyen_lieu    : [],
            list_nhap_kho       : [],
            key_search          : {abc : ""},
        }
    },
    mounted()  {
        this.loadDataNguyenLieu();
        this.loadDataNhapKho();
    },
    methods :   {
        loadDataNguyenLieu()   {
            baseRequest
                .get('admin/nguyen-lieu/lay-du-lieu')
                .then((res) =>  {
                    this.list_nguyen_lieu = res.data.nguyen_lieu;
                });
        },
        loadDataNhapKho()   {
            baseRequest
                .get('admin/nhap-kho/lay-du-lieu')
                .then((res) =>  {
                    this.list_nhap_kho = res.data.nhap_kho;
                });
        },
        searchNguyenLieu() {
            baseRequest
                .post('admin/nguyen-lieu/tim-nguyen-lieu', this.key_search)
                .then((res) =>  {
                    this.list_nguyen_lieu = res.data.nguyen_lieu;
                });
        },
        addnguyenLieu(value){
            baseRequest
                .post('admin/nhap-kho/them-nguyen-lieu',value)
                .then((res) =>  {
                    if(res.data.status == true) {
                        toaster.success('Thông báo<br>' + res.data.message);
                        this.loadDataNhapKho();
                    }
                });
        },
        deletenguyenLieu(value){
            baseRequest
                .delete('admin/nhap-kho/xoa-nguyen-lieu/' + value.id)
                .then((res) =>  {
                    if(res.data.status == true) {
                        toaster.success('Thông báo<br>' + res.data.message);
                        this.loadDataNhapKho();
                    }
                });
        },

        updateNhapKho(value) {  
            baseRequest
                .put('admin/nhap-kho/cap-nhat-nhap-kho', value)
                .then((res) => {
                    if(res.data.status) {
                        toaster.success(res.data.message);
                        this.loadDataNhapKho();
                    } else {
                        toaster.error(res.data.message);
                    }
                })
        }
    },
}
</script>

<style>

</style>