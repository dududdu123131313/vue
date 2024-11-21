<!-- RegistrationComponent.vue -->
<template>
    <div>
      <h1>预约挂号</h1>
      <p>这里是预约挂号的内容。</p>
      <!-- 预约按钮 -->
      <button @click="showModal = true">预约挂号</button>
  
      <!-- 预约信息窗口 -->
      <div v-if="showModal" class="modal">
        <div class="modal-content">
          <!-- 关闭按钮 -->
          <span class="close" @click="showModal = false">&times;</span>
          <h2>预约挂号信息</h2>
          <p>预约时间: {{ appointmentTime }}</p>
          <p>科室: {{ department }}</p>
          <!-- 选择挂号人下拉选择栏 -->
          <label for="registrant">挂号人:</label>
          <select id="registrant" v-model="selectedRegistrant">
            <option v-for="registrant in registrants" :key="registrant" :value="registrant">
              {{ registrant }}
            </option>
          </select>
          <!-- 支付按钮 -->
          <button @click="handlePayment">支付</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        showModal: false,
        department: '内科', // 示例科室
        registrants: ['张三', '李四', '王五'], // 挂号人列表
        selectedRegistrant: '' // 选中的挂号人
      };
    },
    computed: {
      // 计算属性，用于显示当前时间
      appointmentTime() {
        const now = new Date();
        return now.toLocaleTimeString('zh-CN', { hour12: false }) + ' ' + now.toLocaleDateString('zh-CN');
      }
    },
    methods: {
      handlePayment() {
        alert('支付功能尚未实现');
        // 这里可以添加支付逻辑
        this.showModal = false;
      }
    }
  };
  </script>
  
  <style scoped>
  .modal {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
  }
  
  .modal-content {
    background-color: white;
    padding: 20px;
    border-radius: 5px;
    width: 500px; /* 增加窗口的宽度 */
    text-align: center;
    position: relative; /* 添加相对定位 */
  }
  
  .close {
    cursor: pointer;
    position: absolute;
    right: 10px;
    top: 10px; /* 调整关闭按钮的位置 */
    font-size: 25px;
  }
  
  button {
    margin-top: 10px;
  }
  
  label {
    display: block;
    margin-top: 10px;
  }
  
  select {
    width: 100%;
    padding: 10px;
    margin-top: 5px;
    border-radius: 5px;
    border: 1px solid #ccc;
  }
  </style>