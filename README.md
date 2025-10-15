
# Planka là công cụ quản lý dự án mã nguồn mở theo phong cách Kanban, rất phù hợp để áp dụng trong quy trình Scrum.

## 🔧 Chức năng chính của Planka trong Scrum:
- Bảng Kanban: quản lý trạng thái công việc như "To Do", "In Progress", "Code Review", "Done".
- Danh sách và thẻ nhiệm vụ: phân chia công việc theo Sprint hoặc backlog.
- Trường tùy chỉnh: theo dõi Story Points, Priority, Risk Level...
- Quản lý vai trò: phân quyền cho Product Owner, Scrum Master, Developer.
- Nhãn (labels): phân loại Sprint, loại công việc (bug, feature...), trạng thái (blocked...).
- API xuất dữ liệu: hỗ trợ tạo Burn-down chart hoặc phân tích hiệu suất nhóm.

## 📋 Ví dụ cấu hình Planka cho Scrum:
1. Danh sách công việc (Lists):
   - Product Backlog
   - To Do
   - In Progress
   - Code Review
   - Done

2. Trường tùy chỉnh:
   - Story Points: 1, 2, 3, 5, 8, 13 (theo dãy Fibonacci)
   - Priority: Cao / Trung bình / Thấp
   - Risk: Cao / Trung bình / Thấp
   - Sprint: Sprint-YYYYMMDD

3. Vai trò người dùng:
   - Admin: Product Owner
   - Editor: Developer
   - Owner: Scrum Master

4. Nhãn (Labels):
   - Sprint 2025-Q1-S1
   - Bug, Feature, Technical Debt
   - Blocked, In Review

## 🚀 Lợi ích khi dùng Planka cho Scrum:
- Miễn phí, mã nguồn mở, dễ tùy biến.
- Giao diện đơn giản, dễ dùng cho cả nhóm kỹ thuật và phi kỹ thuật.
- Có thể triển khai bằng Docker, tích hợp với CI/CD hoặc các công cụ phân tích.

## 📦 Hướng dẫn triển khai Planka bằng Docker:
1. Tạo file docker-compose.yml với nội dung:

```
   version: "3.8"
   services:
     planka:
       image: ghcr.io/plankanban/planka:latest
       restart: always
       ports:
         - "3000:1337"
       environment:
         - DATABASE_URL=postgres://user:password@db/planka
         - SECRET_KEY=your-secret-key
       depends_on:
         - db

     db:
       image: postgres:14
       restart: always
       environment:
         - POSTGRES_DB=planka
         - POSTGRES_USER=user
         - POSTGRES_PASSWORD=password
       volumes:
         - postgres-data:/var/lib/postgresql/data

   volumes:
     postgres-data:
```

3. Chạy lệnh:
   docker-compose up -d

4. Truy cập Planka tại địa chỉ: http://localhost:3000

