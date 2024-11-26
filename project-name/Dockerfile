# استفاده از تصویر Node.js به عنوان پایه
FROM node:latest

# تنظیم محیط کار
WORKDIR /usr/src/app

# کپی کردن فایل‌های package.json و package-lock.json
COPY package*.json ./

# نصب وابستگی‌ها
RUN npm install --force

# کپی کردن فایل .env (این قسمت را اضافه کردیم)
COPY .env .env

# کپی کردن فایل schema.prisma و دیگر فایل‌های مربوط به Prisma
COPY prisma ./prisma

# ایجاد ساختار دیتابیس توسط Prisma
RUN npx prisma generate --schema=./prisma/schema.prisma

# کپی کردن کدها و فایل‌های پروژه
COPY . .

# پورتی که NestJS از آن استفاده می‌کند را اعلام می‌کنیم (پیش‌فرض 3001)
EXPOSE 3001

# دستوری برای اجرای برنامه Nest.js
CMD ["npm", "start"]
