# 🚫 Invalid Email Formats
## 1️⃣ Missing "@" Symbol
userexample.com
user.example.com
## 2️⃣ Missing or Invalid Domain
user@.com
user@com
user@localhost
user@.ua
user@-example.com (domains can't start with -)
## 3️⃣ Invalid Characters
user@exam!ple.com
user@ex#ample.ua
user@example.ua? (special characters not allowed)
## 4️⃣ Consecutive Dots (".") in Local or Domain Part
user..name@example.com
user@exa..mple.ua
## 5️⃣ Starting or Ending with Special Characters
.user@example.com
user.@example.ua
user-@example.ua
## 6️⃣ Spaces in Email
user name@example.com
user@exa mple.ua
## 7️⃣ Missing Top-Level Domain (TLD)
user@example
user@example.c
## 8️⃣ Invalid Ukrainian Domains
user@example.rus ❌ (Russia-related domains are mostly blocked in Ukraine)
user@example.su ❌ (Soviet-era domains are mostly not used in Ukraine)
## 9️⃣ Cyrillic Letters in Email Address
користувач@пошта.укр (Some Ukrainian services support .укр, but many international platforms reject Cyrillic)
користувач@укр.net (⚠️ Possible issue on international sites)
## 🔟 Missing or Misplaced Quotation Marks
"user"@example.com (valid per RFC, but rejected by many platforms)
user@ "example".com
