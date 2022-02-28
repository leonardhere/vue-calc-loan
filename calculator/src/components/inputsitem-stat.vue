<template>
    <select name="" id="">
        <option value="Значение">Статус клиента</option>
    </select>
</template>

<style scoped>
    select{
        border-radius: 6px;
        background-color: #e6f1fa;
        border: none;
        font-size: 15px;
        letter-spacing: 0.3px;
        height: 48px;
        padding-left: 16px;
        padding-right: 36px;
        margin-right: 20px;
    }
    @media (max-width: 768px){
        select{
            width: 45%;
        }
    }
    @media (max-width: 425px){
        select{
            width: 95%;
            margin-bottom: 20px;
            margin-right: 0;
        }
    }
    
</style>