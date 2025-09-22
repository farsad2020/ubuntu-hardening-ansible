# ubuntu-hardening-ansible
این پروژه یک پلی‌بوک کامل انسیبل برای هاردنینگ سرورهای Ubuntu 24.04 است.
هدف، افزایش امنیت سیستم‌عامل مطابق با بهترین پرکتیس‌ها و نزدیک به CIS Benchmark و پروژه‌هایی مثل konstruktoid/hardening https://github.com/konstruktoid/hardening
ساختار پروژه



ansible-hardening/
│
├── ansible.cfg
├── inventory/
│   └── hosts.ini
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

    
main.yml → پلی‌بوک اصلی که همه رول‌ها را ایمپورت می‌کند.

roles/ → شامل رول‌های مجزا برای هر بخش از هاردنینگ.
چه چیزهایی هاردن می‌شوند؟

Common → آپدیت‌ها، پکیج‌های پایه امنیتی، timezone

Packages → حذف بسته‌های ناامن/غیرضروری (مثل  rsh, tftp)

Firewall → فعال‌سازی UFW با policy امن (deny incoming, allow outgoing)

SSH → غیرفعال کردن RootLogin و PasswordAuth، محدودیت idle session، پیکربندی امن

Sysctl → تنظیمات کرنل (IP redirects, rp_filter, randomize_va_space, suid dumpable و …)

Logging → auditd, journald persistent storage, logrotate

AppArmor → فعال‌سازی AppArmor و اجرای پروفایل‌ها

Users → قفل root، سیاست رمز عبور، sudo policy
