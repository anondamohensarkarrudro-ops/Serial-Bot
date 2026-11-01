# Auto Serial Bot v3.0.0 — Termux-এ চালানোর নিয়ম

1) Termux (F-Droid থেকে) খুলে:
   pkg update -y && pkg install -y python
2) ফোল্ডার বানিয়ে bot.py ও requirements.txt সেখানে রাখুন:
   mkdir -p ~/serialbot && cd ~/serialbot
   (ফাইলগুলো Download থেকে আনতে: termux-setup-storage চালিয়ে cp ~/storage/downloads/bot.py .)
3) লাইব্রেরি: pip install -r requirements.txt
4) .env বানান (নিজের মান বসান):
   cat > .env << 'EOF'
   BOT_TOKEN=...
   LOG_CHANNEL_ID=-100...
   ADMIN_IDS=আপনার_আইডি
   ADMIN_CONTACT=@username
   EOF
5) বটকে লগ চ্যানেলে Admin বানান, তারপর: python bot.py
6) ব্যাকগ্রাউন্ডে: termux-wake-lock && nohup python bot.py > bot.log 2>&1 &
   বন্ধ: pkill -f bot.py   লগ: tail -f bot.log
7) প্রথম কাজ: বটে /addfeed দিয়ে সিরিয়াল যোগ → /settings_admin ও /admin থেকে দাম, bKash/Nagad/Rocket নম্বর সেট করুন।

## নতুন ফিচার (v3.0.0 পরিশিষ্ট)
- Basic/Pro: /admin → সেটিংস → মান থেকে Basic দাম/লিমিট/কোয়ালিটি দিন; ইউজার কার্ডে 🥈 Basic বাটন।
- A/B ওয়েলকাম: ✏️ ওয়েলকাম → 🅰️🅱️ A/B টেস্ট চালু; B-র টেক্সট আলাদা এডিট করুন। ⏰ শিডিউল দিয়ে নির্দিষ্ট সময়ে টেক্সট বদলান।
- অটোপ্লে অ্যাপ্রুভাল: সেটিংস → 🛡 চালু করলে প্রতিটি এপিসোড পাঠানোর আগে আপনার অনুমতি চাইবে।
- SMS অটো-ভেরিফাই: pkg install termux-api + Termux:API অ্যাপ + SMS পারমিশন; /smscheck দিয়ে টেস্ট, তারপর সেটিংসে 📩 চালু।
- প্রোমো সোর্স: /promosrc add সিরিয়াল_আইডি পেজ-লিংক ; /linkcheck দিয়ে সব লিংক/বাটন চেক।
