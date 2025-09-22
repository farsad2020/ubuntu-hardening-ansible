# Ubuntu 24.04 Hardening with Ansible

این پروژه یک **پلی‌بوک کامل انسیبل** برای هاردنینگ سرورهای **Ubuntu 24.04** است.  
هدف، افزایش امنیت سیستم‌عامل مطابق با بهترین پرکتیس‌ها و نزدیک به **CIS Benchmark** و پروژه‌هایی مثل [konstruktoid/hardening](https://github.com/konstruktoid/hardening) می‌باشد.  

---

## 📂 ساختار پروژه




ansible-hardening/
│
├── ansible.cfg
├── inventory/
│ └── hosts.ini
├── main.yml
└── roles/
├── common.yml
├── packages.yml
├── firewall.yml
├── ssh.yml
├── sysctl.yml
├── logging.yml
├── apparmor.yml
└── users.yml

---

## 🔐 چه چیزهایی هاردن می‌شوند؟

- **Common** → آپدیت‌ها، پکیج‌های پایه امنیتی، timezone  
- **Packages** → حذف بسته‌های ناامن/غیرضروری (مثل telnet, rsh, tftp)  
- **Firewall** → فعال‌سازی UFW با policy امن (deny incoming, allow outgoing)  
- **SSH** → غیرفعال کردن RootLogin و PasswordAuth، محدودیت idle session، پیکربندی امن  
- **Sysctl** → تنظیمات کرنل (IP redirects, rp_filter, randomize_va_space, suid dumpable و …)  
- **Logging** → auditd, journald persistent storage, logrotate  
- **AppArmor** → فعال‌سازی AppArmor و اجرای پروفایل‌ها  
- **Users** → قفل root، سیاست رمز عبور، sudo policy  

---

## ⚙️ پیش‌نیازها

- نصب [Ansible](https://docs.ansible.com/) روی ماشین مدیریت (Control Node)  
- دسترسی SSH به سرور Ubuntu 24.04 با کاربر دارای sudo  
- فعال بودن Python روی سرور مقصد (به صورت پیش‌فرض هست)  

---

## 🚀 نحوه استفاده

1. مخزن را کلون کنید یا فایل‌ها را کپی کنید:

   ```bash
   git clone https://github.com/farsad2020/ubuntu-hardening-ansible.git
   cd ubuntu-hardening-ansible
