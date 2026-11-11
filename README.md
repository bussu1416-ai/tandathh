<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>Đạo Cụ Quay Phim: Cùng Một Tin Nhắn, Hai Kết Cục</title>
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts: Inter -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
  <!-- Font Awesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />

  <style>
    * {
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
      -webkit-tap-highlight-color: transparent;
      user-select: none;
    }

    input {
      user-select: text;
    }

    /* Keyframe rung màn hình khi có thông báo */
    @keyframes phoneShake {
      0%, 100% { transform: translate(0, 0) rotate(0deg); }
      15% { transform: translate(-6px, -3px) rotate(-1deg); }
      30% { transform: translate(6px, 2px) rotate(1deg); }
      45% { transform: translate(-6px, 3px) rotate(-1deg); }
      60% { transform: translate(6px, -2px) rotate(1deg); }
      75% { transform: translate(-4px, 2px) rotate(-0.5deg); }
      90% { transform: translate(4px, -1px) rotate(0.5deg); }
    }

    .animate-shake {
      animation: phoneShake 0.55s cubic-bezier(.36,.07,.19,.97) both;
    }

    /* Rung mạnh cho cảnh trừ 5 triệu */
    @keyframes heavyAlertShake {
      0%, 100% { transform: translate(0, 0) scale(1); }
      10%, 30%, 50%, 70%, 90% { transform: translate(-8px, 2px) scale(1.01); }
      20%, 40%, 60%, 80% { transform: translate(8px, -2px) scale(1.01); }
    }

    .animate-heavy-shake {
      animation: heavyAlertShake 0.75s ease-in-out both;
    }

    /* Hiệu ứng trượt thông báo từ trên xuống */
    @keyframes slideDownBanner {
      0% { transform: translateY(-130%) scale(0.95); opacity: 0; }
      100% { transform: translateY(0) scale(1); opacity: 1; }
    }

    .banner-enter {
      animation: slideDownBanner 0.4s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }

    /* Hiệu ứng xuất hiện tin nhắn */
    @keyframes popMessage {
      0% { transform: translateY(24px) scale(0.94); opacity: 0; }
      100% { transform: translateY(0) scale(1); opacity: 1; }
    }

    .msg-enter {
      animation: popMessage 0.35s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }

    /* Nhấp nháy khẩn cấp */
    @keyframes urgentPulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.75; transform: scale(0.98); }
    }

    .urgent-pulse {
      animation: urgentPulse 1s infinite ease-in-out;
    }

    /* Tùy chỉnh thanh cuộn ẩn gọn */
    .no-scrollbar::-webkit-scrollbar {
      display: none;
    }
    .no-scrollbar {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }
  </style>
</head>
<body class="bg-slate-950 text-slate-900 min-h-screen flex items-center justify-center sm:p-4 overflow-hidden">

  <!-- KHUNG ĐIỆN THOẠI CHUẨN 9:16 (Full-screen trên điện thoại thật, có viền máy trên Desktop) -->
  <div id="phoneFrame" class="relative w-full h-[100dvh] sm:w-[412px] sm:h-[860px] sm:max-h-[95vh] sm:aspect-[9/16] bg-white sm:rounded-[44px] sm:shadow-[0_0_60px_rgba(0,0,0,0.85)] sm:border-[10px] sm:border-slate-800 flex flex-col overflow-hidden transition-colors duration-300">

    <!-- Tai thỏ / Dynamic Island giả lập (chỉ hiện nhẹ nhàng để giống thật) -->
    <div class="hidden sm:block absolute top-2 left-1/2 -translate-x-1/2 w-28 h-5 bg-black rounded-full z-50 pointer-events-none"></div>

    <!-- THANH TRẠNG THÁI ĐIỆN THOẠI (STATUS BAR) -->
    <!-- Mẹo: Nhấp đúp vào thanh trạng thái cũng có thể ẩn/hiện thanh đạo cụ -->
    <header id="statusBar" ondblclick="togglePropBar()" title="Nhấp đúp để Ẩn/Hiện thanh đạo cụ" class="w-full px-5 pt-2.5 pb-2 flex items-center justify-between text-xs font-bold z-40 select-none transition-colors duration-300 bg-white text-slate-900">
      <div class="flex items-center gap-1.5">
        <span id="statusClock" class="text-sm font-extrabold tracking-tight">09:41</span>
        <span id="timerDelayBadge" class="hidden px-1.5 py-0.5 text-[10px] bg-amber-500 text-white rounded-full animate-pulse">3s...</span>
      </div>
      <div class="flex items-center gap-2 text-xs">
        <i class="fa-solid fa-signal"></i>
        <span class="font-extrabold text-[11px]">5G</span>
        <i class="fa-solid fa-wifi"></i>
        <div class="flex items-center gap-0.5">
          <span class="text-[11px] font-bold">92%</span>
          <i class="fa-solid fa-battery-full text-sm"></i>
        </div>
      </div>
    </header>

    <!-- ĐỒNG HỒ ĐẾM NGƯỢC 15:00 Ở GÓC (Dùng cho Cảnh 2 & Cảnh 3) -->
    <div id="globalCountdownWidget" class="fixed sm:absolute top-12 right-3 z-40 bg-red-600 text-white px-3 py-1.5 rounded-2xl shadow-lg border-2 border-white flex items-center gap-2 urgent-pulse">
      <i class="fa-solid fa-stopwatch text-sm"></i>
      <div class="leading-none">
        <div class="text-[9px] uppercase font-bold tracking-wider opacity-90">Hạn xác thực</div>
        <div id="globalCountdownText" class="text-base font-black tracking-wider tabular-nums">15:00</div>
      </div>
    </div>

    <!-- BANNER THÔNG BÁO NỔI TỪ ĐỈNH MÀN HÌNH (Push Notification cho SMS / OTP / Trừ tiền) -->
    <div id="pushNotificationBanner" class="hidden absolute top-11 left-3 right-3 z-50 bg-slate-900/95 backdrop-blur-md text-white p-3.5 rounded-2xl shadow-2xl border border-slate-700 cursor-pointer" onclick="handleBannerClick()">
      <div class="flex items-start gap-3">
        <div id="pushIconBox" class="w-10 h-10 rounded-xl bg-blue-600 flex items-center justify-center shrink-0 text-lg">
          <i class="fa-solid fa-comment-sms"></i>
        </div>
        <div class="flex-1 min-w-0">
          <div class="flex items-center justify-between">
            <span id="pushSender" class="font-extrabold text-sm text-amber-400 tracking-wide">[Ngân hàng] • Tin nhắn SMS</span>
            <span class="text-[11px] text-slate-300 font-semibold">Bây giờ</span>
          </div>
          <p id="pushBody" class="text-sm font-semibold text-white mt-1 leading-snug">
            [Ngân hàng] Tài khoản của bạn bị khóa do bất thường...
          </p>
          <span id="pushHint" class="inline-block mt-1.5 text-[11px] font-bold text-sky-400 underline">Chạm để mở / điền nhanh</span>
        </div>
      </div>
    </div>

    <!-- ========================================== -->
    <!-- KHU VỰC NỘI DUNG 5 MÀN HÌNH ĐẠO CỤ          -->
    <!-- ========================================== -->
    <main class="flex-1 flex flex-col overflow-y-auto no-scrollbar relative">

      <!-- ============================================================== -->
      <!-- MÀN HÌNH 1: CẢNH 2 - TIN NHẮN ĐẾN (ỨNG DỤNG TIN NHẮN SMS)        -->
      <!-- ============================================================== -->
      <section id="screen-1" class="flex-1 flex flex-col bg-slate-100 h-full">
        <!-- Header ứng dụng SMS -->
        <div class="bg-white border-b border-slate-200 px-4 py-3 flex items-center justify-between shadow-sm">
          <div class="flex items-center gap-3">
            <button class="text-blue-600 text-lg font-bold flex items-center gap-1">
              <i class="fa-solid fa-chevron-left"></i>
              <span class="text-xs font-bold bg-blue-100 text-blue-700 px-2 py-0.5 rounded-full">1</span>
            </button>
            <div class="w-10 h-10 rounded-full bg-gradient-to-br from-blue-600 to-indigo-700 text-white flex items-center justify-center font-black text-base shadow-sm">
              NH
            </div>
            <div>
              <div class="flex items-center gap-1.5">
                <h1 class="font-black text-base text-slate-900 tracking-tight">[Ngân hàng]</h1>
                <span class="text-[10px] font-bold bg-slate-200 text-slate-700 px-1.5 py-0.5 rounded">SMS</span>
              </div>
              <p class="text-xs text-slate-500 font-medium">Tin nhắn dịch vụ • Hôm nay</p>
            </div>
          </div>
          <button onclick="switchScreen(5)" title="Xem chi tiết / Chặn số (Cảnh của Bình)" class="w-9 h-9 rounded-full bg-slate-100 hover:bg-slate-200 flex items-center justify-center text-slate-700">
            <i class="fa-solid fa-circle-info text-lg"></i>
          </button>
        </div>

        <!-- Nội dung khung chat SMS -->
        <div class="flex-1 p-4 space-y-4 overflow-y-auto flex flex-col">
          <div class="text-center my-1">
            <span class="text-xs font-bold text-slate-500 bg-slate-200/80 px-3 py-1 rounded-full">
              Hôm nay, 09:40
            </span>
          </div>

          <!-- Tin nhắn cũ bình thường để tạo độ chân thực -->
          <div class="max-w-[88%] self-start bg-white border border-slate-200 rounded-2xl rounded-tl-sm p-3.5 shadow-sm text-slate-700 text-sm font-medium leading-relaxed">
            <span class="font-bold text-slate-900">[Ngân hàng]</span> Thông báo: Quý khách vừa đăng nhập thành công trên ứng dụng [Ngân hàng] SmartBanking lúc 08:15.
          </div>

          <!-- Trạng thái chờ kích hoạt tin nhắn đến -->
          <div id="scamSmsPlaceholder" class="hidden my-auto py-8 text-center">
            <div class="inline-flex flex-col items-center p-5 rounded-2xl bg-white border-2 border-dashed border-slate-300 shadow-sm max-w-xs">
              <i class="fa-solid fa-bell-concierge text-3xl text-amber-500 mb-2"></i>
              <p class="text-sm font-bold text-slate-800">Đang chờ tin nhắn lừa đảo đến...</p>
              <p class="text-xs text-slate-500 mt-1 mb-3">Bấm nút bên dưới để phát tiếng "Ting!" và hiện tin nhắn ngay hoặc hẹn giờ 3 giây để diễn viên chuẩn bị.</p>
              <div class="flex gap-2 w-full">
                <button onclick="triggerScamSms()" class="flex-1 bg-blue-600 hover:bg-blue-700 text-white font-extrabold text-xs py-2.5 px-3 rounded-xl shadow">
                  <i class="fa-solid fa-volume-high mr-1"></i> Nổ tin nhắn ngay
                </button>
                <button onclick="triggerDelayedAction(triggerScamSms, 3)" class="bg-amber-500 hover:bg-amber-600 text-white font-extrabold text-xs py-2.5 px-3 rounded-xl shadow">
                  <i class="fa-regular fa-clock mr-1"></i> Hẹn 3s
                </button>
              </div>
            </div>
          </div>

          <!-- TIN NHẮN LỪA ĐẢO CHÍNH TRONG KỊCH BẢN (Chữ to, độ tương phản cao cho B-roll) -->
          <div id="scamSmsBubble" class="msg-enter max-w-[95%] self-start bg-white border-2 border-red-500 rounded-2xl rounded-tl-sm p-4 shadow-md relative">
            <div class="flex items-center justify-between mb-1.5">
              <span class="inline-flex items-center gap-1 text-xs font-extrabold uppercase tracking-wider text-red-600 bg-red-50 px-2 py-0.5 rounded-md border border-red-200">
                <i class="fa-solid fa-triangle-exclamation"></i> Cảnh báo khẩn
              </span>
              <span class="text-xs font-bold text-slate-400">Vừa xong</span>
            </div>

            <p class="text-[17px] font-bold text-slate-900 leading-relaxed">
              <span class="font-black text-red-600">[Ngân hàng]</span> Tài khoản của bạn bị khóa do bất thường. Bấm vào link
              <button onclick="goToFakeWebFromSms()" class="inline text-left font-black text-blue-600 underline decoration-2 underline-offset-4 hover:text-blue-800 active:scale-95 transition-transform bg-blue-50 px-1.5 py-0.5 rounded">
                xacthuc-taikhoan.example
              </button>
              để xác thực trong <span class="text-red-600 font-black underline">15 phút</span>, nếu không sẽ bị đóng vĩnh viễn.
            </p>

            <!-- Thẻ preview link giả giúp ngón tay diễn viên An dễ bấm trúng khi quay cận cảnh -->
            <div onclick="goToFakeWebFromSms()" class="mt-3 bg-blue-50/90 hover:bg-blue-100 active:bg-blue-200 border-2 border-blue-400 rounded-xl p-3 cursor-pointer transition flex items-center justify-between group">
              <div class="min-w-0 pr-2">
                <div class="text-[11px] font-extrabold text-blue-700 uppercase tracking-wide flex items-center gap-1">
                  <i class="fa-solid fa-globe"></i> Liên kết xác thực tài khoản
                </div>
                <div class="text-sm font-black text-blue-700 underline truncate mt-0.5">
                  https://xacthuc-taikhoan.example
                </div>
                <div class="text-xs font-semibold text-slate-600 mt-0.5">
                  Bấm vào đây để mở cổng xác thực [Ngân hàng]
                </div>
              </div>
              <div class="w-10 h-10 rounded-xl bg-blue-600 text-white flex items-center justify-center shrink-0 shadow group-active:scale-90 transition">
                <i class="fa-solid fa-arrow-up-right-from-square"></i>
              </div>
            </div>
          </div>

          <!-- Nút kích hoạt nhanh dành cho lúc tập dượt (Tự ẩn khi ẩn thanh đạo cụ) -->
          <div class="prop-helper-ui mt-auto pt-2 flex flex-wrap gap-2">
            <button onclick="triggerScamSms()" class="flex-1 bg-indigo-600 active:bg-indigo-700 text-white font-extrabold text-xs py-2.5 px-3 rounded-xl shadow flex items-center justify-center gap-1.5">
              <i class="fa-solid fa-bell"></i> Kích hoạt tin nhắn đến (Ting!)
            </button>
            <button onclick="triggerDelayedAction(triggerScamSms, 3)" class="bg-amber-500 active:bg-amber-600 text-white font-extrabold text-xs py-2.5 px-3 rounded-xl shadow flex items-center justify-center gap-1" title="Ẩn rồi đợi 3 giây tự kêu Ting!">
              <i class="fa-solid fa-hourglass-half"></i> Hẹn 3s nổ
            </button>
          </div>
        </div>

        <!-- Thanh soạn tin nhắn giả ở đáy -->
        <div class="bg-white border-t border-slate-200 px-3 py-2.5 flex items-center gap-2 text-slate-400">
          <i class="fa-solid fa-circle-plus text-xl text-slate-400"></i>
          <div class="flex-1 bg-slate-100 rounded-full px-4 py-2 text-xs font-semibold text-slate-400 border border-slate-200">
            Không thể trả lời tin nhắn dịch vụ này
          </div>
          <i class="fa-solid fa-microphone text-lg"></i>
        </div>
      </section>

      <!-- ============================================================== -->
      <!-- MÀN HÌNH 2: CẢNH 3 CỦA AN - TRANG WEB GIẢ & NHẬP MÃ OTP         -->
      <!-- ============================================================== -->
      <section id="screen-2" class="hidden flex-1 flex flex-col bg-slate-50 h-full">
        <!-- Thanh địa chỉ trình duyệt giả cảnh báo Không bảo mật -->
        <div class="bg-slate-900 text-white px-3 py-2.5 border-b-2 border-red-500 shadow-md">
          <div class="flex items-center gap-2 bg-slate-800 border border-red-500/80 rounded-xl px-3 py-2">
            <span class="inline-flex items-center gap-1 text-red-400 font-black text-xs shrink-0">
              <i class="fa-solid fa-triangle-exclamation"></i> Không bảo mật
            </span>
            <span class="text-slate-500 font-bold">|</span>
            <span class="text-sm font-black text-white tracking-tight truncate">
              xacthuc-taikhoan.example
            </span>
            <i class="fa-solid fa-rotate-right text-xs text-slate-400 ml-auto"></i>
          </div>
        </div>

        <!-- Banner đếm ngược đỏ nhấp nháy báo hiệu khẩn cấp -->
        <div class="bg-red-600 text-white px-4 py-2.5 flex items-center justify-between shadow-inner">
          <div class="flex items-center gap-2">
            <i class="fa-solid fa-circle-exclamation text-lg animate-bounce"></i>
            <span class="text-xs font-extrabold uppercase tracking-wide leading-tight">
              Xác thực trong 15 phút trước khi khóa vĩnh viễn!
            </span>
          </div>
          <span id="fakeWebTimer" class="bg-black/30 px-2.5 py-1 rounded-lg font-black text-base tabular-nums border border-white/30">
            14:59
          </span>
        </div>

        <!-- Nội dung chính của Trang Web Giả -->
        <div class="flex-1 p-4 overflow-y-auto flex flex-col justify-between">
          <div>
            <!-- Logo & Header ngân hàng giả mạo -->
            <div class="bg-white rounded-2xl p-4 border-2 border-slate-200 shadow-sm mb-4 text-center">
              <div class="w-12 h-12 rounded-2xl bg-gradient-to-tr from-red-600 to-orange-500 text-white flex items-center justify-center mx-auto mb-2 shadow-md text-xl font-black">
                <i class="fa-solid fa-building-columns"></i>
              </div>
              <h2 class="text-lg font-black text-slate-900 uppercase tracking-tight">
                CỔNG XÁC THỰC [NGÂN HÀNG]
              </h2>
              <p class="text-xs font-bold text-red-600 mt-0.5">
                ⚠️ Yêu cầu xác minh danh tính khẩn cấp để mở khóa tài khoản
              </p>
            </div>

            <!-- BƯỚC 1: FORM ĐĂNG NHẬP GIẢ -->
            <div id="fakeWebStep1" class="bg-white rounded-2xl p-4 border-2 border-slate-200 shadow-md space-y-4">
              <div class="flex items-center justify-between border-b border-slate-100 pb-2">
                <span class="text-xs font-black uppercase text-slate-500">Bước 1/2: Thông tin đăng nhập</span>
                <span class="text-[11px] font-bold text-red-600 bg-red-50 px-2 py-0.5 rounded border border-red-200">
                  Bắt buộc
                </span>
              </div>

              <!-- Ô nhập Số tài khoản / Tên đăng nhập (Tự nhập tay) -->
              <div>
                <label for="fakeUsernameInput" class="block text-xs font-extrabold text-slate-700 uppercase mb-1.5">
                  Số tài khoản / Tên đăng nhập
                </label>
                <div class="relative">
                  <input
                    id="fakeUsernameInput"
                    type="text"
                    autocomplete="off"
                     autocorrect="off"
                    autocapitalize="off"
                    spellcheck="false"
                    placeholder="Nhập số tài khoản..."
                    class="w-full pl-3.5 pr-10 py-3 text-base font-black text-slate-900 bg-slate-50 border-2 border-slate-300 rounded-xl focus:border-red-500 focus:bg-white focus:outline-none tracking-wider"
                  />
                  <i class="fa-solid fa-user text-slate-400 absolute right-3.5 top-1/2 -translate-y-1/2 pointer-events-none"></i>
                </div>
              </div>

              <!-- Ô nhập Mật khẩu (Tự nhập tay + Nút ẩn/hiện mật khẩu) -->
              <div>
                <label for="fakePasswordInput" class="block text-xs font-extrabold text-slate-700 uppercase mb-1.5">
                  Mật khẩu Internet Banking
                </label>
                <div class="relative">
                  <input
                    id="fakePasswordInput"
                    type="password"
                    autocomplete="off"
                    placeholder="Nhập mật khẩu..."
                    class="w-full pl-3.5 pr-10 py-3 text-base font-black text-slate-900 bg-slate-50 border-2 border-slate-300 rounded-xl focus:border-red-500 focus:bg-white focus:outline-none tracking-wider"
                  />
                  <button
                    type="button"
                    onclick="toggleFakePasswordVisibility()"
                    class="text-slate-400 hover:text-slate-600 absolute right-3 top-1/2 -translate-y-1/2 p-1"
                    title="Ẩn/Hiện mật khẩu"
                  >
                    <i id="fakePasswordEyeIcon" class="fa-solid fa-eye"></i>
                  </button>
                </div>
              </div>

              <!-- Nút TIẾP TỤC XÁC THỰC -->
              <button
                type="button"
                onclick="submitFakeLoginStep1()"
                class="w-full py-4 rounded-xl bg-gradient-to-r from-red-600 to-orange-600 hover:from-red-700 hover:to-orange-700 active:scale-[0.98] text-white font-black text-base uppercase tracking-wider shadow-lg shadow-red-600/30 flex items-center justify-center gap-2 transition"
              >
                <span>TIẾP TỤC XÁC THỰC</span>
                <i class="fa-solid fa-arrow-right"></i>
              </button>
            </div>

            <!-- BƯỚC 2: NHẬP MÃ OTP GIẢ (Tự nhập bằng bàn phím) -->
            <div id="fakeWebStep2" class="hidden bg-white rounded-2xl p-4 border-2 border-red-400 shadow-md space-y-4">
              <div class="flex items-center justify-between border-b border-slate-100 pb-2">
                <span class="text-xs font-black uppercase text-red-600">Bước 2/2: Nhập mã xác thực OTP</span>
                <button
                  type="button"
                  onclick="resetFakeWeb()"
                  class="text-[11px] font-bold text-slate-500 hover:text-slate-800 underline"
                >
                  Quay lại
                </button>
              </div>

              <!-- Thông báo tin nhắn OTP gửi về để diễn viên nhìn và tự gõ -->
              <div class="bg-amber-50 border border-amber-300 rounded-xl p-3 text-left">
                <div class="flex items-center justify-between text-[11px] font-extrabold text-amber-800 uppercase mb-1">
                  <span><i class="fa-solid fa-comment-sms mr-1"></i>Tin nhắn SMS vừa đến</span>
                  <span>Bây giờ</span>
                </div>
                <p class="text-xs font-bold text-slate-800 leading-snug">
                  [Ngân hàng]: Mã OTP xác thực giao dịch của quý khách là <span class="text-red-600 font-black text-sm underline">123456</span>.
                </p>
              </div>

              <!-- Ô nhập 6 số OTP to rõ cho máy quay (Tự gõ bàn phím) -->
              <div>
                <label for="fakeOtpInput" class="block text-center text-xs font-extrabold text-slate-600 uppercase mb-2">
                  NHẬP MÃ OTP
                </label>
                <input
                  id="fakeOtpInput"
                  type="text"
                  maxlength="6"
                  inputmode="numeric"
                  autocomplete="off"
                  placeholder="Nhập 6 số OTP..."
                  class="w-full py-3.5 px-4 text-center text-2xl font-black tracking-[0.35em] text-red-600 bg-slate-50 border-2 border-red-500 rounded-xl focus:outline-none focus:ring-4 focus:ring-red-200 placeholder:text-sm placeholder:tracking-normal placeholder:font-semibold placeholder:text-slate-400"
                />
              </div>

              <!-- Bàn phím số ảo tùy chọn nếu diễn viên muốn bấm trực tiếp trên màn hình -->
              <div class="grid grid-cols-3 gap-1.5 pt-1">
                <button type="button" onclick="appendOtpDigit('1')" class="py-2 bg-slate-100 active:bg-slate-300 rounded-xl font-black text-base text-slate-800">1</button>
                <button type="button" onclick="appendOtpDigit('2')" class="py-2 bg-slate-100 active:bg-slate-300 rounded-xl font-black text-base text-slate-800">2</button>
                <button type="button" onclick="appendOtpDigit('3')" class="py-2 bg-slate-100 active:bg-slate-300 rounded-xl font-black text-base text-slate-800">3</button>
                <button type="button" onclick="appendOtpDigit('4')" class="py-2 bg-slate-100 active:bg-slate-300 rounded-xl font-black text-base text-slate-800">4</button>
                <button type="button" onclick="appendOtpDigit('5')" class="py-2 bg-slate-100 active:bg-slate-300 rounded-xl font-black text-base text-slate-800">5</button>
                <button type="button" onclick="appendOtpDigit('6')" class="py-2 bg-slate-100 active:bg-slate-300 rounded-xl font-black text-base text-slate-800">6</button>
                <button type="button" onclick="appendOtpDigit('7')" class="py-2 bg-slate-100 active:bg-slate-300 rounded-xl font-black text-base text-slate-800">7</button>
                <button type="button" onclick="appendOtpDigit('8')" class="py-2 bg-slate-100 active:bg-slate-300 rounded-xl font-black text-base text-slate-800">8</button>
                <button type="button" onclick="appendOtpDigit('9')" class="py-2 bg-slate-100 active:bg-slate-300 rounded-xl font-black text-base text-slate-800">9</button>
                <button type="button" onclick="clearOtpDigits()" class="py-2 bg-slate-200 active:bg-slate-300 rounded-xl font-bold text-xs text-slate-700">Xóa hết</button>
                <button type="button" onclick="appendOtpDigit('0')" class="py-2 bg-slate-100 active:bg-slate-300 rounded-xl font-black text-base text-slate-800">0</button>
                <button type="button" onclick="backspaceOtpDigit()" class="py-2 bg-slate-200 active:bg-slate-300 rounded-xl font-bold text-base text-slate-700">
                  <i class="fa-solid fa-delete-left"></i>
                </button>
              </div>

              <button
                type="button"
                onclick="completeFakeOtpStep2()"
                class="w-full py-4 rounded-xl bg-gradient-to-r from-red-600 to-orange-600 active:scale-[0.98] text-white font-black text-base uppercase tracking-wider shadow-lg flex items-center justify-center gap-2 transition"
              >
                <i class="fa-solid fa-check-double"></i>
                <span>XÁC NHẬN HOÀN TẤT</span>
              </button>
            </div>

            <!-- BƯỚC 3: ĐANG XỬ LÝ GIẢ MẠO (Sau khi An bấm xác nhận OTP) -->
            <div id="fakeWebStep3" class="hidden bg-white rounded-2xl p-6 border-2 border-red-500 shadow-lg text-center space-y-4">
              <div class="w-16 h-16 rounded-full border-4 border-red-600 border-t-transparent animate-spin mx-auto"></div>
              <h3 class="text-lg font-black text-slate-900">ĐANG ĐỒNG BỘ XÁC THỰC...</h3>
              <p class="text-sm font-bold text-red-600 bg-red-50 p-3 rounded-xl border border-red-200">
                Hệ thống đang xử lý phiên đăng nhập. Vui lòng không tắt trình duyệt!
              </p>
              <button onclick="resetFakeWeb()" class="text-xs font-bold text-slate-500 underline pt-2">
                Quay lại Bước 1 (Quay lại cảnh)
              </button>
            </div>
          </div>

          <p class="text-center text-[11px] font-semibold text-slate-400 mt-4">
            © Cổng xác thực tự động • xacthuc-taikhoan.example
          </p>
        </div>
      </section>

      <!-- ============================================================== -->
      <!-- MÀN HÌNH 3: CẢNH 3 CỦA BÌNH - APP [NGÂN HÀNG] CHÍNH THỨC        -->
      <!-- ============================================================== -->
      <section id="screen-3" class="hidden flex-1 flex flex-col bg-slate-50 h-full">
        <!-- Header xanh tin cậy của App chính thức -->
        <div class="bg-gradient-to-br from-emerald-700 via-teal-700 to-cyan-800 text-white p-4 pb-6 rounded-b-3xl shadow-lg">
          <div class="flex items-center justify-between mb-4">
            <div class="flex items-center gap-2.5">
              <div class="w-10 h-10 rounded-xl bg-white/15 backdrop-blur flex items-center justify-center border border-white/30 text-emerald-300 text-xl">
                <i class="fa-solid fa-shield-halved"></i>
              </div>
              <div>
                <div class="text-sm font-black tracking-wide uppercase flex items-center gap-1">
                  [Ngân hàng] SmartBanking
                  <i class="fa-solid fa-circle-check text-emerald-300 text-xs"></i>
                </div>
                <div class="text-[11px] text-emerald-100 font-medium">Ứng dụng chính thức • Bảo mật 2 lớp</div>
              </div>
            </div>
            <div class="px-2.5 py-1 rounded-full bg-emerald-500/30 border border-emerald-300/40 text-[11px] font-extrabold flex items-center gap-1">
              <i class="fa-solid fa-lock text-[10px]"></i> An toàn
            </div>
          </div>

          <!-- Thẻ thông tin tài khoản của Bình -->
          <div class="bg-white text-slate-900 rounded-2xl p-4 shadow-xl border-2 border-emerald-400">
            <div class="flex items-center justify-between border-b border-slate-100 pb-2.5 mb-2.5">
              <div>
                <span class="text-[10px] font-extrabold uppercase tracking-wider text-slate-400 block">Chủ tài khoản (Chạm để sửa)</span>
                <div contenteditable="true" spellcheck="false" class="text-base font-black text-slate-900 uppercase tracking-tight focus:outline-none focus:bg-yellow-50 rounded px-0.5">
                  NGUYỄN VĂN BÌNH
                </div>
              </div>
              <div class="text-right">
                <span class="text-[10px] font-extrabold uppercase tracking-wider text-slate-400 block">Số tài khoản</span>
                <span class="text-sm font-black text-teal-700 tracking-wider">0123 456 789</span>
              </div>
            </div>

            <!-- Huy hiệu trạng thái hoạt động bình thường -->
            <div class="bg-emerald-50 border-2 border-emerald-500 rounded-xl p-2.5 mb-3 flex items-center gap-2.5">
              <div class="w-8 h-8 rounded-lg bg-emerald-600 text-white flex items-center justify-center shrink-0 text-base">
                <i class="fa-solid fa-check"></i>
              </div>
              <div class="text-xs font-black text-emerald-900 leading-snug">
                ✅ ĐANG HOẠT ĐỘNG BÌNH THƯỜNG
                <span class="block text-[11px] font-bold text-emerald-700">(Không có cảnh báo khóa)</span>
              </div>
            </div>

            <!-- Số dư khả dụng -->
            <div class="flex items-baseline justify-between bg-slate-50 px-3.5 py-2.5 rounded-xl border border-slate-200">
              <span class="text-xs font-extrabold text-slate-600 uppercase">Số dư khả dụng:</span>
              <span class="text-2xl font-black text-emerald-700 tracking-tight">5.000.000 đ</span>
            </div>
          </div>
        </div>

        <!-- Phần thân App: Cảnh báo an toàn & Nút gọi Hotline -->
        <div class="flex-1 p-4 space-y-3.5 overflow-y-auto">
          <!-- Banner nhắc nhở an toàn nổi bật -->
          <div class="bg-amber-50 border-2 border-amber-400 rounded-2xl p-3.5 shadow-sm">
            <div class="flex items-start gap-2.5">
              <div class="w-9 h-9 rounded-xl bg-amber-500 text-white flex items-center justify-center shrink-0 text-base mt-0.5">
                <i class="fa-solid fa-bullhorn"></i>
              </div>
              <div>
                <h3 class="text-xs font-black uppercase text-amber-900 tracking-wide">
                  Khuyến cáo an ninh mạng
                </h3>
                <p class="text-sm font-extrabold text-slate-900 mt-1 leading-snug">
                  <span class="text-red-600 font-black">[Ngân hàng] KHÔNG BAO GIỜ</span> yêu cầu nhập mật khẩu và mã OTP qua đường link tin nhắn.
                </p>
              </div>
            </div>
          </div>

          <!-- Lưới tính năng ngân hàng -->
          <div class="grid grid-cols-3 gap-2.5 text-center">
            <div class="bg-white p-3 rounded-2xl border border-slate-200 shadow-sm">
              <i class="fa-solid fa-money-bill-transfer text-teal-600 text-lg mb-1"></i>
              <div class="text-xs font-bold text-slate-700">Chuyển tiền</div>
            </div>
            <div class="bg-white p-3 rounded-2xl border border-slate-200 shadow-sm">
              <i class="fa-solid fa-qrcode text-teal-600 text-lg mb-1"></i>
              <div class="text-xs font-bold text-slate-700">Quét mã QR</div>
            </div>
            <div class="bg-white p-3 rounded-2xl border border-slate-200 shadow-sm">
              <i class="fa-solid fa-credit-card text-teal-600 text-lg mb-1"></i>
              <div class="text-xs font-bold text-slate-700">Quản lý thẻ</div>
            </div>
          </div>

          <!-- Nút gọi Hotline chính thức in ở mặt sau thẻ -->
          <div class="bg-white rounded-2xl p-3.5 border-2 border-teal-600 shadow-sm">
            <div class="flex items-center justify-between">
              <div>
                <div class="text-xs font-extrabold text-teal-800 uppercase">Tổng đài CSKH 24/7 (Trên mặt sau thẻ)</div>
                <div class="text-lg font-black text-slate-900">1900 0000 <span class="text-xs font-bold text-emerald-600">(Chính thức)</span></div>
              </div>
              <button onclick="toggleHotlineCallModal(true)" class="bg-teal-600 active:bg-teal-700 text-white font-black text-xs px-4 py-3 rounded-xl shadow flex items-center gap-1.5">
                <i class="fa-solid fa-phone-volume"></i> Gọi kiểm tra
              </button>
            </div>
          </div>
        </div>

        <!-- Giao diện giả lập đang gọi Hotline khi Bình bấm nút Gọi -->
        <div id="hotlineCallModal" class="hidden absolute inset-0 bg-slate-900/95 backdrop-blur-md text-white z-40 flex flex-col items-center justify-between py-12 px-6 text-center">
          <div>
            <span class="px-3 py-1 rounded-full bg-emerald-500/20 text-emerald-300 text-xs font-bold border border-emerald-400/30">
              Cuộc gọi xác minh an toàn
            </span>
            <h3 class="text-2xl font-black mt-4">Hotline [Ngân hàng]</h3>
            <p class="text-lg font-extrabold text-emerald-400 mt-1">1900 0000</p>
            <p class="text-sm text-slate-300 mt-2">Đang kết nối tổng đài viên... (00:08)</p>
          </div>
          <div class="w-24 h-24 rounded-full bg-emerald-600/30 border-2 border-emerald-400 flex items-center justify-center text-4xl text-emerald-300 animate-pulse">
            <i class="fa-solid fa-headset"></i>
          </div>
          <button onclick="toggleHotlineCallModal(false)" class="w-16 h-16 rounded-full bg-red-600 text-white text-2xl flex items-center justify-center shadow-lg">
            <i class="fa-solid fa-phone-slash"></i>
          </button>
        </div>
      </section>

      <!-- ============================================================== -->
      <!-- MÀN HÌNH 4: CẢNH 4 CỦA AN - 24 GIỜ SAU (-5.000.000đ)           -->
      <!-- ============================================================== -->
      <section id="screen-4" class="hidden flex-1 flex flex-col bg-slate-950 text-white h-full relative">
        <!-- Nền cảnh báo đỏ tối phục vụ quay cận cảnh -->
        <div class="p-4 flex-1 flex flex-col justify-between overflow-y-auto">
          <!-- Đồng hồ màn hình khóa / 24 giờ sau -->
          <div class="text-center pt-2 pb-3 border-b border-slate-800">
            <span class="inline-block px-3 py-0.5 rounded-full bg-red-950 text-red-300 border border-red-700 text-[11px] font-black uppercase tracking-widest mb-1">
              24 GIỜ SAU
            </span>
            <div class="text-4xl font-black tracking-tight text-white">09:42</div>
            <div class="text-xs font-semibold text-slate-400">Thông báo khẩn cấp từ hệ thống</div>
          </div>

          <!-- CARD THÔNG BÁO BIẾN ĐỘNG SỐ DƯ CỰC TO, ĐỘ TƯƠNG PHẢN CAO -->
          <div id="deductionAlertCard" class="my-auto bg-white text-slate-900 rounded-3xl p-5 border-4 border-red-600 shadow-[0_0_50px_rgba(220,38,38,0.65)] space-y-4">
            <!-- Tiêu đề cảnh báo -->
            <div class="flex items-center justify-between border-b-2 border-red-100 pb-3">
              <div class="flex items-center gap-2">
                <div class="w-10 h-10 rounded-xl bg-red-600 text-white flex items-center justify-center text-xl shrink-0">
                  <i class="fa-solid fa-triangle-exclamation"></i>
                </div>
                <div>
                  <h2 class="text-sm font-black uppercase text-red-600 tracking-tight">
                    ⚠️ BIẾN ĐỘNG SỐ DƯ - [Ngân hàng]
                  </h2>
                  <p class="text-xs font-bold text-slate-500">Vừa xong • Giao dịch trực tuyến</p>
                </div>
              </div>
            </div>

            <!-- SỐ TIỀN BỊ TRỪ CỰC LỚN ĐỂ LÊN HÌNH RÕ NÉT -->
            <div class="bg-red-50 border-2 border-red-500 rounded-2xl p-4 text-center">
              <span class="text-xs font-black uppercase text-red-700 tracking-wider block mb-1">
                Số tiền giao dịch
              </span>
              <div class="text-4xl sm:text-[42px] font-black text-red-600 tracking-tight leading-none py-1">
                -5.000.000đ
              </div>
            </div>

            <!-- Chi tiết Tài khoản & Số dư cuối 0đ -->
            <div class="space-y-2.5 text-sm bg-slate-50 p-3.5 rounded-2xl border border-slate-200">
              <div class="flex items-center justify-between">
                <span class="font-bold text-slate-500">Tài khoản:</span>
                <span class="font-black text-slate-900 text-base">0123xxx999</span>
              </div>
              <div class="flex items-center justify-between border-t border-slate-200 pt-2">
                <span class="font-bold text-slate-500">Số dư cuối:</span>
                <span class="font-black text-red-600 text-xl bg-red-100 px-2.5 py-0.5 rounded-lg border border-red-300">
                  0đ
                </span>
              </div>
              <div class="border-t border-slate-200 pt-2">
                <span class="font-bold text-slate-500 block text-xs uppercase mb-1">Nội dung giao dịch:</span>
                <div class="font-black text-slate-900 text-sm bg-amber-100/80 border border-amber-300 px-2.5 py-1.5 rounded-lg tracking-wide">
                  CHUYEN TIEN QUA LIEN KET XAC THUC
                </div>
              </div>
            </div>

            <!-- Cảnh báo đăng nhập thiết bị lạ -->
            <div class="text-xs font-bold text-red-700 bg-red-100/80 px-3 py-2 rounded-xl flex items-center gap-2">
              <i class="fa-solid fa-user-secret text-base"></i>
              <span>Thực hiện bởi thiết bị lạ sau khi xác thực OTP.</span>
            </div>
          </div>

          <!-- Nút kích hoạt thông báo trừ tiền kèm rung và còi báo (Tự ẩn khi ẩn thanh đạo cụ) -->
          <div class="prop-helper-ui pt-3 flex gap-2">
            <button onclick="triggerBalanceDeductionAlert()" class="flex-1 bg-red-600 active:bg-red-700 text-white font-black text-xs py-3 px-3 rounded-xl shadow-lg flex items-center justify-center gap-1.5 border border-red-400">
              <i class="fa-solid fa-bolt"></i> Kích hoạt thông báo trừ tiền (Ting!)
            </button>
            <button onclick="triggerDelayedAction(triggerBalanceDeductionAlert, 3)" class="bg-amber-500 active:bg-amber-600 text-slate-950 font-black text-xs py-3 px-3 rounded-xl shadow-lg flex items-center justify-center gap-1">
              <i class="fa-solid fa-clock"></i> Hẹn 3s
            </button>
          </div>
        </div>
      </section>

      <!-- ============================================================== -->
      <!-- MÀN HÌNH 5: CẢNH 4 CỦA BÌNH - CHẶN SỐ LẠ & BÁO CÁO TIN RÁC      -->
      <!-- ============================================================== -->
      <section id="screen-5" class="hidden flex-1 flex flex-col bg-slate-100 h-full relative">
        <!-- Header chi tiết người gửi -->
        <div class="bg-white border-b border-slate-200 p-4 text-center shadow-sm">
          <div class="w-14 h-14 rounded-full bg-red-100 text-red-600 border-2 border-red-300 flex items-center justify-center mx-auto mb-2 text-2xl font-black">
            <i class="fa-solid fa-user-slash"></i>
          </div>
          <h2 class="text-base font-black text-slate-900">
            [Ngân hàng] <span class="text-red-600">(Số lạ: +84 999 xxx 000)</span>
          </h2>
          <p class="text-xs font-bold text-amber-700 bg-amber-100 inline-block px-2.5 py-0.5 rounded-full mt-1 border border-amber-300">
            ⚠️ Số điện thoại không thuộc danh bạ chính thức
          </p>
        </div>

        <div class="flex-1 p-4 space-y-4 overflow-y-auto flex flex-col justify-between">
          <!-- Nội dung tin nhắn lừa đảo trích dẫn -->
          <div class="bg-white p-3.5 rounded-2xl border-2 border-slate-300 shadow-sm">
            <div class="text-[11px] font-extrabold uppercase text-slate-400 mb-1">Nội dung tin nhắn nghi vấn:</div>
            <p class="text-sm font-bold text-slate-800 leading-snug">
              "[Ngân hàng] Tài khoản của bạn bị khóa do bất thường. Bấm vào link <span class="text-blue-600 underline">xacthuc-taikhoan.example</span> để xác thực trong 15 phút, nếu không sẽ bị đóng vĩnh viễn."
            </p>
          </div>

          <!-- TRẠNG THÁI 1: 2 NÚT HÀNH ĐỘNG LỚN ĐỂ QUAY CẬN CẢNH NGÓN TAY BÌNH -->
          <div id="blockReportActions" class="space-y-3 my-auto">
            <div class="text-xs font-extrabold uppercase text-slate-500 text-center tracking-wider">
              Chọn thao tác xử lý an toàn
            </div>

            <!-- Nút 1: Chặn người gửi này -->
            <button
              onclick="openBlockConfirmModal('block')"
              class="w-full py-4 px-4 bg-white hover:bg-red-50 active:scale-[0.98] text-red-600 border-2 border-red-500 rounded-2xl font-black text-base shadow-md flex items-center justify-between transition"
            >
              <span class="flex items-center gap-3">
                <span class="w-10 h-10 rounded-xl bg-red-100 text-red-600 flex items-center justify-center text-lg">🚫</span>
                <span>Chặn người gửi này</span>
              </span>
              <i class="fa-solid fa-chevron-right"></i>
            </button>

            <!-- Nút 2: Báo cáo tin nhắn rác / Lừa đảo -->
            <button
              onclick="openBlockConfirmModal('report')"
              class="w-full py-4 px-4 bg-red-600 hover:bg-red-700 active:scale-[0.98] text-white rounded-2xl font-black text-base shadow-lg flex items-center justify-between transition"
            >
              <span class="flex items-center gap-3">
                <span class="w-10 h-10 rounded-xl bg-white/20 text-white flex items-center justify-center text-lg">🚩</span>
                <span>Báo cáo tin nhắn rác / Lừa đảo</span>
              </span>
              <i class="fa-solid fa-chevron-right"></i>
            </button>
          </div>

          <!-- TRẠNG THÁI 2: ĐÃ CHẶN & BÁO CÁO THÀNH CÔNG -->
          <div id="blockReportSuccess" class="hidden my-auto bg-emerald-50 border-3 border-emerald-500 rounded-3xl p-5 text-center shadow-lg space-y-3">
            <div class="w-16 h-16 rounded-full bg-emerald-600 text-white flex items-center justify-center text-3xl mx-auto shadow-md">
              <i class="fa-solid fa-check"></i>
            </div>
            <h3 class="text-lg font-black text-emerald-950 leading-snug">
              ✅ Đã chặn số & Gửi báo cáo tin nhắn rác thành công
            </h3>
            <p class="text-xs font-bold text-emerald-800 leading-relaxed">
              Số lạ <span class="underline">+84 999 xxx 000</span> đã bị đưa vào danh sách chặn và gửi cảnh báo lừa đảo đến hệ thống chống tin nhắn rác.
            </p>
            <button onclick="resetScreen5()" class="text-xs font-extrabold text-emerald-700 underline pt-1">
              Hoàn tác để quay lại cảnh bấm nút
            </button>
          </div>

          <!-- Căn cứ pháp luật hiển thị gọn phía dưới hỗ trợ Cảnh 5 -->
          <div class="bg-blue-950 text-white p-3.5 rounded-2xl border border-blue-700 text-xs space-y-1">
            <div class="font-black text-amber-400 uppercase flex items-center gap-1.5">
              <i class="fa-solid fa-scale-balanced"></i> Căn cứ pháp luật (Cảnh 5)
            </div>
            <p class="font-semibold text-blue-100 leading-snug">
              • <strong class="text-white">Luật An ninh mạng 2025</strong> có hiệu lực từ ngày <strong class="text-amber-300">01/07/2026</strong>.
            </p>
            <p class="font-semibold text-blue-100 leading-snug">
              • Hành vi lừa đảo có thể bị xử lý hình sự theo <strong class="text-amber-300">Điều 174 Bộ luật Hình sự</strong>.
            </p>
          </div>
        </div>

        <!-- Hộp thoại xác nhận Chặn & Báo cáo -->
        <div id="confirmBlockModal" class="hidden absolute inset-0 bg-slate-950/75 backdrop-blur-sm z-40 flex items-center justify-center p-5">
          <div class="bg-white rounded-3xl p-5 w-full max-w-sm border-2 border-slate-200 shadow-2xl space-y-4 text-center msg-enter">
            <div class="w-12 h-12 rounded-2xl bg-red-100 text-red-600 flex items-center justify-center mx-auto text-2xl">
              <i class="fa-solid fa-shield-virus"></i>
            </div>
            <h3 class="text-lg font-black text-slate-900">
              Xác nhận chặn & báo cáo lừa đảo?
            </h3>
            <p class="text-xs font-bold text-slate-600 leading-relaxed">
              Chặn vĩnh viễn số <span class="text-slate-900 font-black">+84 999 xxx 000</span> và gửi nội dung tin nhắn giả mạo <span class="text-red-600 font-black">[Ngân hàng]</span> tới hệ thống tiếp nhận tin rác.
            </p>
            <div class="flex gap-2.5 pt-1">
              <button onclick="closeBlockConfirmModal()" class="flex-1 py-3 rounded-xl bg-slate-100 font-extrabold text-xs text-slate-700">
                Hủy
              </button>
              <button onclick="confirmBlockAndReport()" class="flex-1 py-3 rounded-xl bg-red-600 text-white font-black text-xs shadow-md">
                Xác nhận ngay
              </button>
            </div>
          </div>
        </div>
      </section>

    </main>

    <!-- ============================================================== -->
    <!-- THANH ĐIỀU KHIỂN ĐẠO CỤ (PROP SWITCHER)                         -->
    <!-- ============================================================== -->
    <nav id="propControlBar" class="bg-slate-900/95 backdrop-blur-md text-white border-t border-slate-700 px-2.5 py-2 z-50 transition-all duration-200">
      <!-- Dòng 1: Các nút công cụ nhanh (Ting, Đồng hồ 15:00, Reset, Ẩn thanh đạo cụ) -->
      <div class="flex items-center justify-between gap-1.5 mb-2">
        <button
          onclick="playTingAndShake()"
          class="bg-amber-500 hover:bg-amber-400 active:scale-95 text-slate-950 font-black text-[11px] px-2.5 py-1.5 rounded-lg flex items-center gap-1 shadow"
        >
          <i class="fa-solid fa-volume-high"></i> Phát "Ting!"
        </button>

        <button
          id="toggleTimerBtn"
          onclick="toggleCountdownWidget()"
          class="bg-red-600/90 hover:bg-red-600 text-white font-bold text-[11px] px-2.5 py-1.5 rounded-lg flex items-center gap-1 border border-red-400/40"
        >
          <i class="fa-solid fa-stopwatch"></i> 15:00: Bật
        </button>

        <button
          onclick="resetCurrentScreen()"
          title="Đặt lại màn hình hiện tại để quay đúp mới"
          class="bg-slate-800 hover:bg-slate-700 text-slate-200 font-bold text-[11px] px-2.5 py-1.5 rounded-lg flex items-center gap-1 border border-slate-600"
        >
          <i class="fa-solid fa-rotate-left"></i> Reset
        </button>

        <button
          onclick="togglePropBar()"
          class="bg-slate-700 hover:bg-slate-600 text-amber-300 font-extrabold text-[11px] px-2.5 py-1.5 rounded-lg flex items-center gap-1 border border-amber-400/40 ml-auto"
        >
          <i class="fa-solid fa-eye-slash"></i> Ẩn thanh
        </button>
      </div>

      <!-- Dòng 2: 5 nút chuyển nhanh qua 5 màn hình theo kịch bản -->
      <div class="grid grid-cols-5 gap-1">
        <button onclick="switchScreen(1)" id="tab-btn-1" class="prop-tab-btn py-1.5 px-1 rounded-lg text-center border transition flex flex-col items-center justify-center">
          <span class="text-[11px] font-black">1. SMS</span>
          <span class="text-[9px] opacity-80 truncate w-full">Cảnh 2</span>
        </button>
        <button onclick="switchScreen(2)" id="tab-btn-2" class="prop-tab-btn py-1.5 px-1 rounded-lg text-center border transition flex flex-col items-center justify-center">
          <span class="text-[11px] font-black">2. Web Giả</span>
          <span class="text-[9px] opacity-80 truncate w-full">Cảnh 3 An</span>
        </button>
        <button onclick="switchScreen(3)" id="tab-btn-3" class="prop-tab-btn py-1.5 px-1 rounded-lg text-center border transition flex flex-col items-center justify-center">
          <span class="text-[11px] font-black">3. App Thật</span>
          <span class="text-[9px] opacity-80 truncate w-full">Cảnh 3 Bình</span>
        </button>
        <button onclick="switchScreen(4)" id="tab-btn-4" class="prop-tab-btn py-1.5 px-1 rounded-lg text-center border transition flex flex-col items-center justify-center">
          <span class="text-[11px] font-black">4. -5 Triệu</span>
          <span class="text-[9px] opacity-80 truncate w-full">Cảnh 4 An</span>
        </button>
        <button onclick="switchScreen(5)" id="tab-btn-5" class="prop-tab-btn py-1.5 px-1 rounded-lg text-center border transition flex flex-col items-center justify-center">
          <span class="text-[11px] font-black">5. Chặn Số</span>
          <span class="text-[9px] opacity-80 truncate w-full">Cảnh 4 Bình</span>
        </button>
      </div>
    </nav>

    <!-- NÚT CHẤM NHỎ MỜ Ở GÓC DƯỚI BÊN PHẢI KHI ẨN THANH ĐẠO CỤ (Không bị lộ khi quay B-roll) -->
    <button
      id="hiddenPropDot"
      onclick="togglePropBar()"
      title="Hiện lại thanh điều khiển đạo cụ"
      class="hidden absolute bottom-2 right-2 z-50 w-7 h-7 rounded-full bg-slate-900/20 hover:bg-slate-900/80 text-white/40 hover:text-white flex items-center justify-center text-[10px] border border-white/20 transition"
    >
      <i class="fa-solid fa-sliders"></i>
    </button>

    <!-- Thanh Home Indicator giả lập ở đáy điện thoại -->
    <div class="bg-transparent py-1.5 flex justify-center pointer-events-none">
      <div class="w-32 h-1 bg-slate-400/50 rounded-full"></div>
    </div>
  </div>

  <!-- ============================================================== -->
  <!-- JAVASCRIPT XỬ LÝ ÂM THANH WEB AUDIO API & LOGIC ĐẠO CỤ          -->
  <!-- ============================================================== -->
  <script>
    // Trạng thái toàn cục
    let currentScreen = 1;
    let propBarVisible = true;
    let countdownVisible = true;
    let countdownSeconds = 15 * 60; // 15 phút = 900 giây
    let countdownInterval = null;
    let bannerTimeout = null;
    let audioCtx = null;

    // Khởi tạo Web Audio API để tạo âm thanh "Ting!" và âm báo khẩn cấp không cần file ngoài
    function getAudioContext() {
      if (!audioCtx) {
        const AudioContextClass = window.AudioContext || window.webkitAudioContext;
        audioCtx = new AudioContextClass();
      }
      if (audioCtx.state === 'suspended') {
        audioCtx.resume();
      }
      return audioCtx;
    }

    // Phát tiếng "Ting!" thông báo tin nhắn SMS điện thoại chân thực
    function playSmsTingSound() {
      try {
        const ctx = getAudioContext();
        const now = ctx.currentTime;

        // Nốt 1 (C6)
        const osc1 = ctx.createOscillator();
        const gain1 = ctx.createGain();
        osc1.type = 'sine';
        osc1.frequency.setValueAtTime(1046.5, now);
        gain1.gain.setValueAtTime(0.001, now);
        gain1.gain.exponentialRampToValueAtTime(0.35, now + 0.015);
        gain1.gain.exponentialRampToValueAtTime(0.001, now + 0.25);
        osc1.connect(gain1);
        gain1.connect(ctx.destination);
        osc1.start(now);
        osc1.stop(now + 0.26);

        // Nốt 2 cao và ngân (G6 - Tạo tiếng "Ting!" trong trẻo)
        const osc2 = ctx.createOscillator();
        const gain2 = ctx.createGain();
        osc2.type = 'triangle';
        osc2.frequency.setValueAtTime(1567.98, now + 0.11);
        gain2.gain.setValueAtTime(0.001, now + 0.11);
        gain2.gain.exponentialRampToValueAtTime(0.45, now + 0.13);
        gain2.gain.exponentialRampToValueAtTime(0.0008, now + 0.85);
        osc2.connect(gain2);
        gain2.connect(ctx.destination);
        osc2.start(now + 0.11);
        osc2.stop(now + 0.86);
      } catch (e) {
        console.warn('Web Audio API error:', e);
      }
    }

    // Phát âm thanh cảnh báo khẩn cấp khi bị trừ -5.000.000đ
    function playUrgentAlertSound() {
      try {
        const ctx = getAudioContext();
        const now = ctx.currentTime;

        [0, 0.18, 0.36].forEach((offset, idx) => {
          const osc = ctx.createOscillator();
          const gain = ctx.createGain();
          osc.type = 'sawtooth';
          osc.frequency.setValueAtTime(idx === 2 ? 880 : 660, now + offset);
          gain.gain.setValueAtTime(0.01, now + offset);
          gain.gain.exponentialRampToValueAtTime(0.3, now + offset + 0.02);
          gain.gain.exponentialRampToValueAtTime(0.001, now + offset + 0.15);
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.start(now + offset);
          osc.stop(now + offset + 0.16);
        });
      } catch (e) {
        console.warn('Audio error:', e);
      }
    }

    // Hiệu ứng rung màn hình + rung vật lý trên điện thoại Android (nếu hỗ trợ)
    function triggerScreenShake(heavy = false) {
      const frame = document.getElementById('phoneFrame');
      const cls = heavy ? 'animate-heavy-shake' : 'animate-shake';
      frame.classList.remove('animate-shake', 'animate-heavy-shake');
      void frame.offsetWidth; // Reflow
      frame.classList.add(cls);

      if (navigator.vibrate) {
        navigator.vibrate(heavy ? [200, 80, 250, 80, 300] : [120, 60, 150]);
      }

      setTimeout(() => {
        frame.classList.remove(cls);
      }, 800);
    }

    // Nút phát tiếng "Ting!" chung trên thanh công cụ
    function playTingAndShake() {
      playSmsTingSound();
      triggerScreenShake(false);
    }

    // Hẹn giờ 3 giây để diễn viên đặt máy xuống bàn trước khi thông báo tự nổ
    function triggerDelayedAction(callback, seconds = 3) {
      const badge = document.getElementById('timerDelayBadge');
      let remaining = seconds;
      badge.textContent = `${remaining}s...`;
      badge.classList.remove('hidden');

      const timer = setInterval(() => {
        remaining--;
        if (remaining > 0) {
          badge.textContent = `${remaining}s...`;
        } else {
          clearInterval(timer);
          badge.classList.add('hidden');
          callback();
        }
      }, 1000);
    }

    // Hiển thị Banner thông báo trượt từ đỉnh màn hình xuống
    let currentBannerAction = null;
    function showTopPushBanner({ sender, body, hint, iconClass = 'fa-comment-sms', bgClass = 'bg-blue-600', onClick = null }) {
      const banner = document.getElementById('pushNotificationBanner');
      const iconBox = document.getElementById('pushIconBox');
      document.getElementById('pushSender').textContent = sender;
      document.getElementById('pushBody').textContent = body;
      document.getElementById('pushHint').textContent = hint || 'Chạm để xem chi tiết';
      iconBox.className = `w-10 h-10 rounded-xl ${bgClass} flex items-center justify-center shrink-0 text-lg text-white`;
      iconBox.innerHTML = `<i class="fa-solid ${iconClass}"></i>`;

      currentBannerAction = onClick;
      banner.classList.remove('hidden', 'banner-enter');
      void banner.offsetWidth;
      banner.classList.add('banner-enter');

      if (bannerTimeout) clearTimeout(bannerTimeout);
      bannerTimeout = setTimeout(() => {
        banner.classList.add('hidden');
      }, 6500);
    }

    function handleBannerClick() {
      const banner = document.getElementById('pushNotificationBanner');
      banner.classList.add('hidden');
      if (typeof currentBannerAction === 'function') {
        currentBannerAction();
      }
    }

    // Đồng hồ đếm ngược 15:00
    function startCountdownTimer() {
      if (countdownInterval) clearInterval(countdownInterval);
      countdownInterval = setInterval(() => {
        if (countdownSeconds > 0) {
          countdownSeconds--;
        } else {
          countdownSeconds = 15 * 60;
        }
        updateCountdownDisplay();
      }, 1000);
    }

    function updateCountdownDisplay() {
      const mins = String(Math.floor(countdownSeconds / 60)).padStart(2, '0');
      const secs = String(countdownSeconds % 60).padStart(2, '0');
      const formatted = `${mins}:${secs}`;
      const globalEl = document.getElementById('globalCountdownText');
      const fakeWebEl = document.getElementById('fakeWebTimer');
      if (globalEl) globalEl.textContent = formatted;
      if (fakeWebEl) fakeWebEl.textContent = formatted;
    }

    function toggleCountdownWidget() {
      countdownVisible = !countdownVisible;
      const widget = document.getElementById('globalCountdownWidget');
      const btn = document.getElementById('toggleTimerBtn');
      if (countdownVisible) {
        widget.classList.remove('hidden');
        btn.innerHTML = '<i class="fa-solid fa-stopwatch"></i> 15:00: Bật';
        btn.className = 'bg-red-600/90 hover:bg-red-600 text-white font-bold text-[11px] px-2.5 py-1.5 rounded-lg flex items-center gap-1 border border-red-400/40';
      } else {
        widget.classList.add('hidden');
        btn.innerHTML = '<i class="fa-solid fa-stopwatch"></i> 15:00: Tắt';
        btn.className = 'bg-slate-800 hover:bg-slate-700 text-slate-300 font-bold text-[11px] px-2.5 py-1.5 rounded-lg flex items-center gap-1 border border-slate-600';
      }
    }

    // Ẩn / Hiện thanh điều khiển đạo cụ (Prop Switcher)
    function togglePropBar() {
      propBarVisible = !propBarVisible;
      const bar = document.getElementById('propControlBar');
      const dot = document.getElementById('hiddenPropDot');
      const helpers = document.querySelectorAll('.prop-helper-ui');

      if (propBarVisible) {
        bar.classList.remove('hidden');
        dot.classList.add('hidden');
        helpers.forEach(el => el.classList.remove('hidden'));
      } else {
        bar.classList.add('hidden');
        dot.classList.remove('hidden');
        helpers.forEach(el => el.classList.add('hidden'));
      }
    }

    // Chuyển đổi qua lại giữa 5 màn hình
    function switchScreen(screenNumber) {
      currentScreen = screenNumber;
      for (let i = 1; i <= 5; i++) {
        const sec = document.getElementById(`screen-${i}`);
        const btn = document.getElementById(`tab-btn-${i}`);
        if (i === screenNumber) {
          sec.classList.remove('hidden');
          btn.className = 'prop-tab-btn py-1.5 px-1 rounded-lg text-center border transition flex flex-col items-center justify-center bg-blue-600 text-white border-blue-400 shadow';
        } else {
          sec.classList.add('hidden');
          btn.className = 'prop-tab-btn py-1.5 px-1 rounded-lg text-center border transition flex flex-col items-center justify-center bg-slate-800 text-slate-300 border-slate-700 hover:bg-slate-700';
        }
      }

      // Đổi màu thanh trạng thái trên cùng cho hợp với từng màn hình
      const statusBar = document.getElementById('statusBar');
      if (screenNumber === 2 || screenNumber === 4) {
        statusBar.className = 'w-full px-5 pt-2.5 pb-2 flex items-center justify-between text-xs font-bold z-40 select-none transition-colors duration-300 bg-slate-900 text-white';
      } else if (screenNumber === 3) {
        statusBar.className = 'w-full px-5 pt-2.5 pb-2 flex items-center justify-between text-xs font-bold z-40 select-none transition-colors duration-300 bg-emerald-700 text-white';
      } else {
        statusBar.className = 'w-full px-5 pt-2.5 pb-2 flex items-center justify-between text-xs font-bold z-40 select-none transition-colors duration-300 bg-white text-slate-900';
      }

      // Ẩn đồng hồ 15:00 ở màn hình 3, 4, 5 nếu không cần thiết, tự bật ở màn hình 1
      const widget = document.getElementById('globalCountdownWidget');
      if (screenNumber === 1 && countdownVisible) {
        widget.classList.remove('hidden');
      } else {
        widget.classList.add('hidden');
      }

      // Ẩn banner đang mở nếu chuyển cảnh
      document.getElementById('pushNotificationBanner').classList.add('hidden');
    }

    // ==========================================
    // LOGIC MÀN HÌNH 1: KÍCH HOẠT TIN NHẮN ĐẾN
    // ==========================================
    function triggerScamSms() {
      const bubble = document.getElementById('scamSmsBubble');
      const placeholder = document.getElementById('scamSmsPlaceholder');
      placeholder.classList.add('hidden');

      bubble.classList.remove('hidden', 'msg-enter');
      void bubble.offsetWidth;
      bubble.classList.add('msg-enter');

      // Đặt lại đồng hồ 15:00
      countdownSeconds = 15 * 60;
      updateCountdownDisplay();

      playSmsTingSound();
      triggerScreenShake(false);

      showTopPushBanner({
        sender: '[Ngân hàng] • Tin nhắn SMS',
        body: '[Ngân hàng] Tài khoản của bạn bị khóa do bất thường. Bấm vào link xacthuc-taikhoan.example để xác thực trong 15 phút...',
        hint: 'Chạm vào link để mở xacthuc-taikhoan.example',
        iconClass: 'fa-comment-sms',
        bgClass: 'bg-red-600',
        onClick: () => goToFakeWebFromSms()
      });
    }

    function goToFakeWebFromSms() {
      resetFakeWeb();
      switchScreen(2);
    }

    // ==========================================
    // LOGIC MÀN HÌNH 2: TRANG WEB GIẢ & NHẬP OTP
    // ==========================================
    function toggleFakePasswordVisibility() {
      const passInput = document.getElementById('fakePasswordInput');
      const eyeIcon = document.getElementById('fakePasswordEyeIcon');
      if (passInput.type === 'password') {
        passInput.type = 'text';
        eyeIcon.className = 'fa-solid fa-eye-slash';
      } else {
        passInput.type = 'password';
        eyeIcon.className = 'fa-solid fa-eye';
      }
    }

    function submitFakeLoginStep1() {
      document.getElementById('fakeWebStep1').classList.add('hidden');
      document.getElementById('fakeWebStep2').classList.remove('hidden');
      const otpInput = document.getElementById('fakeOtpInput');
      otpInput.value = '';

      // Sau 0.5 giây, trượt thông báo SMS mã OTP 123456 kèm tiếng "Ting!" (không tự động điền)
      setTimeout(() => {
        playSmsTingSound();
        triggerScreenShake(false);
        showTopPushBanner({
          sender: '[Ngân hàng] • Mã xác thực OTP',
          body: '[Ngân hàng]: Mã OTP xác thực giao dịch của quý khách là 123456. Tuyệt đối không cung cấp cho ai.',
          hint: 'Chạm để đóng thông báo và tự nhập mã OTP',
          iconClass: 'fa-key',
          bgClass: 'bg-amber-500',
          onClick: () => {
            otpInput.focus();
          }
        });
      }, 500);
    }

    function appendOtpDigit(digit) {
      const otpInput = document.getElementById('fakeOtpInput');
      if (otpInput.value.length < 6) {
        otpInput.value += digit;
      }
    }

    function backspaceOtpDigit() {
      const otpInput = document.getElementById('fakeOtpInput');
      otpInput.value = otpInput.value.slice(0, -1);
    }

    function clearOtpDigits() {
      document.getElementById('fakeOtpInput').value = '';
    }

    function completeFakeOtpStep2() {
      document.getElementById('fakeWebStep2').classList.add('hidden');
      document.getElementById('fakeWebStep3').classList.remove('hidden');
    }

    function resetFakeWeb() {
      document.getElementById('fakeUsernameInput').value = '';
      const passInput = document.getElementById('fakePasswordInput');
      passInput.value = '';
      passInput.type = 'password';
      const eyeIcon = document.getElementById('fakePasswordEyeIcon');
      if (eyeIcon) eyeIcon.className = 'fa-solid fa-eye';
      document.getElementById('fakeOtpInput').value = '';
      document.getElementById('fakeWebStep1').classList.remove('hidden');
      document.getElementById('fakeWebStep2').classList.add('hidden');
      document.getElementById('fakeWebStep3').classList.add('hidden');
    }

    // ==========================================
    // LOGIC MÀN HÌNH 3: APP NGÂN HÀNG CHÍNH THỨC
    // ==========================================
    function toggleHotlineCallModal(show) {
      const modal = document.getElementById('hotlineCallModal');
      if (show) {
        modal.classList.remove('hidden');
      } else {
        modal.classList.add('hidden');
      }
    }

    // ==========================================
    // LOGIC MÀN HÌNH 4: THÔNG BÁO TRỪ -5.000.000Đ
    // ==========================================
    function triggerBalanceDeductionAlert() {
      const card = document.getElementById('deductionAlertCard');
      card.classList.remove('msg-enter');
      void card.offsetWidth;
      card.classList.add('msg-enter');

      playUrgentAlertSound();
      triggerScreenShake(true);

      showTopPushBanner({
        sender: '⚠️ BIẾN ĐỘNG SỐ DƯ - [Ngân hàng]',
        body: 'Tài khoản 0123xxx999 vừa bị trừ -5.000.000đ. Số dư cuối: 0đ.',
        hint: 'Nội dung: CHUYEN TIEN QUA LIEN KET XAC THUC',
        iconClass: 'fa-triangle-exclamation',
        bgClass: 'bg-red-600'
      });
    }

    // ==========================================
    // LOGIC MÀN HÌNH 5: CHẶN SỐ & BÁO CÁO RÁC
    // ==========================================
    function openBlockConfirmModal() {
      document.getElementById('confirmBlockModal').classList.remove('hidden');
    }

    function closeBlockConfirmModal() {
      document.getElementById('confirmBlockModal').classList.add('hidden');
    }

    function confirmBlockAndReport() {
      closeBlockConfirmModal();
      playSmsTingSound();
      document.getElementById('blockReportActions').classList.add('hidden');
      document.getElementById('blockReportSuccess').classList.remove('hidden');
    }

    function resetScreen5() {
      document.getElementById('blockReportActions').classList.remove('hidden');
      document.getElementById('blockReportSuccess').classList.add('hidden');
      closeBlockConfirmModal();
    }

    // Đặt lại màn hình hiện tại để quay lại nhiều đúp (2-3 lần)
    function resetCurrentScreen() {
      document.getElementById('pushNotificationBanner').classList.add('hidden');
      if (currentScreen === 1) {
        // Ẩn tin nhắn lừa đảo để diễn viên bấm nổ lại từ đầu
        document.getElementById('scamSmsBubble').classList.add('hidden');
        document.getElementById('scamSmsPlaceholder').classList.remove('hidden');
        countdownSeconds = 15 * 60;
        updateCountdownDisplay();
      } else if (currentScreen === 2) {
        resetFakeWeb();
      } else if (currentScreen === 3) {
        toggleHotlineCallModal(false);
      } else if (currentScreen === 4) {
        triggerBalanceDeductionAlert();
      } else if (currentScreen === 5) {
        resetScreen5();
      }
    }

    // Khởi chạy ứng dụng khi tải trang
    window.onload = function () {
      switchScreen(1);
      startCountdownTimer();
    };
  </script>
</body>
</html>
