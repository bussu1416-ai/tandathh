<!DOCTYPE html>
<html lang="vi" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TANDAT ENGLISH - Khóa Học Tiếng Anh Cho Người Mới Bắt Đầu</title>
    <meta name="description" content="TANDAT ENGLISH - khóa học tiếng Anh cho người mới bắt đầu, lộ trình rõ ràng, học thử flashcard miễn phí. Đăng ký tư vấn ngay.">
    <meta name="keywords" content="học tiếng Anh, tiếng Anh cho người mới bắt đầu, khóa học tiếng Anh, TANDAT ENGLISH, Cao Lãnh, Đồng Tháp">
    <meta name="robots" content="index, follow">
    <meta property="og:type" content="website">
    <meta property="og:title" content="TANDAT ENGLISH - Khóa Học Tiếng Anh Cho Người Mới Bắt Đầu">
    <meta property="og:description" content="Khóa học tiếng Anh cho người mới bắt đầu, học thử flashcard miễn phí.">
    <meta property="og:locale" content="vi_VN">
    
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Google Fonts: Plus Jakarta Sans & Inter (Hỗ trợ tiếng Việt sắc nét) -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Plus+Jakarta+Sans:wght@600;700;800&display=swap" rel="stylesheet">
    
    <!-- Font Awesome 6 Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <!-- Cấu hình Tailwind tùy chỉnh màu sắc và font chữ -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        heading: ['Plus Jakarta Sans', 'sans-serif'],
                    },
                    colors: {
                        brand: {
                            50: '#eff6ff',
                            100: '#dbeafe',
                            500: '#3b82f6',
                            600: '#2563eb',
                            700: '#1d4ed8',
                            800: '#1e40af',
                            900: '#1e3a8a',
                        },
                        accent: {
                            50: '#fff7ed',
                            100: '#ffedd5',
                            500: '#f97316',
                            600: '#ea580c',
                            700: '#c2410c',
                        }
                    },
                    boxShadow: {
                        'soft': '0 10px 40px -10px rgba(30, 58, 138, 0.12)',
                        'glow': '0 10px 30px -5px rgba(249, 115, 22, 0.45)',
                    }
                }
            }
        }
    </script>

    <style>
        /* Hiệu ứng Flip Card 3D cho phần Học thử Flashcard */
        .perspective-1000 {
            perspective: 1000px;
        }
        .transform-style-3d {
            transform-style: preserve-3d;
            transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .backface-hidden {
            backface-visibility: hidden;
            -webkit-backface-visibility: hidden;
        }
        .rotate-y-180 {
            transform: rotateY(180deg);
        }
        .flipped {
            transform: rotateY(180deg);
        }

        /* Hiệu ứng sóng âm khi phát âm thanh */
        @keyframes soundWave {
            0%, 100% { height: 6px; }
            50% { height: 20px; }
        }
        .wave-bar {
            animation: soundWave 0.8s ease-in-out infinite;
        }
        .wave-bar:nth-child(2) { animation-delay: 0.15s; }
        .wave-bar:nth-child(3) { animation-delay: 0.3s; }
        .wave-bar:nth-child(4) { animation-delay: 0.45s; }

        /* Tùy chỉnh thanh cuộn */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        ::-webkit-scrollbar-thumb {
            background: #94a3b8;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #64748b;
        }
    </style>
</head>
<body class="font-sans text-slate-800 bg-slate-50 antialiased selection:bg-accent-500 selection:text-white">

    <!-- Thanh thông báo ưu đãi đầu trang (Top Bar) -->
    <div class="bg-brand-900 text-white text-xs sm:text-sm py-2.5 px-4 text-center relative z-50">
        <div class="max-w-7xl mx-auto flex flex-wrap items-center justify-center gap-2 sm:gap-4">
            <span class="inline-flex items-center gap-1.5 bg-accent-500 text-white font-bold px-2.5 py-0.5 rounded-full text-xs uppercase tracking-wider">
                <i class="fa-solid fa-bolt"></i> TANDAT ENGLISH Khai giảng
            </span>
            <p class="font-medium">
                Tặng học bổng <strong class="text-amber-300 underline">40% học phí</strong> & Bộ Flashcard 1.000 từ thông dụng cho 20 học viên đăng ký sớm nhất!
            </p>
        </div>
    </div>

    <!-- 1. STICKY NAVIGATION BAR -->
    <header id="navbar" class="sticky top-0 z-40 bg-white/95 backdrop-blur-md border-b border-slate-200/80 transition-all duration-300">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-20">
                <!-- Logo TANDAT ENGLISH -->
                <a href="#" class="flex items-center gap-3 group">
                    <div class="w-11 h-11 rounded-xl bg-gradient-to-br from-brand-800 to-accent-500 flex items-center justify-center text-white shadow-md group-hover:scale-105 transition-transform">
                        <i class="fa-solid fa-graduation-cap text-xl"></i>
                    </div>
                    <div>
                        <span class="font-heading font-extrabold text-xl tracking-tight text-brand-900 block leading-none">
                            TANDAT <span class="text-accent-600">ENGLISH</span>
                        </span>
                        <span class="text-[11px] font-semibold text-slate-500 tracking-wider uppercase block mt-0.5">
                            Tiếng Anh Cho Người Mới Bắt Đầu
                        </span>
                    </div>
                </a>

                <!-- Desktop Menu Links -->
                <nav class="hidden lg:flex items-center gap-7 text-sm font-semibold text-slate-600">
                    <a href="#loi-ich" class="hover:text-brand-700 transition-colors py-2">Lợi ích</a>
                    <a href="#hoc-thu" class="hover:text-brand-700 transition-colors py-2 flex items-center gap-1.5">
                        <span>Học thử</span>
                        <span class="bg-emerald-100 text-emerald-700 text-[10px] font-bold px-2 py-0.5 rounded-full">Tương tác</span>
                    </a>
                    <a href="#lo-trinh" class="hover:text-brand-700 transition-colors py-2">Lộ trình 90 ngày</a>
                    <a href="#hoc-phi" class="hover:text-brand-700 transition-colors py-2">Học phí</a>
                    <a href="#cam-nhan" class="hover:text-brand-700 transition-colors py-2">Học viên</a>
                    <a href="#dang-ky" class="hover:text-brand-700 transition-colors py-2">Đăng ký ngay</a>
                </nav>

                <!-- CTA Button Desktop -->
                <div class="hidden sm:flex items-center gap-3">
                    <a href="#dang-ky" class="bg-accent-500 hover:bg-accent-600 text-white font-heading font-bold text-sm px-5 py-3 rounded-xl shadow-glow hover:-translate-y-0.5 transition-all flex items-center gap-2">
                        <span>Đăng ký ngay</span>
                        <i class="fa-solid fa-arrow-right text-xs"></i>
                    </a>
                </div>

                <!-- Mobile Hamburger Button -->
                <button id="mobile-menu-btn" onclick="toggleMobileMenu()" aria-label="Mở menu" class="lg:hidden p-2.5 rounded-xl text-slate-700 hover:bg-slate-100 focus:outline-none">
                    <i id="mobile-menu-icon" class="fa-solid fa-bars text-xl"></i>
                </button>
            </div>
        </div>

        <!-- Mobile Menu Dropdown -->
        <div id="mobile-menu" class="hidden lg:hidden bg-white border-b border-slate-200 px-4 pt-2 pb-6 space-y-2 shadow-xl">
            <a href="#loi-ich" onclick="toggleMobileMenu()" class="block px-4 py-2.5 rounded-xl font-semibold text-slate-700 hover:bg-brand-50 hover:text-brand-700">Lợi ích & Phương pháp</a>
            <a href="#hoc-thu" onclick="toggleMobileMenu()" class="block px-4 py-2.5 rounded-xl font-semibold text-slate-700 hover:bg-brand-50 hover:text-brand-700">Học thử & Test trình độ</a>
            <a href="#lo-trinh" onclick="toggleMobileMenu()" class="block px-4 py-2.5 rounded-xl font-semibold text-slate-700 hover:bg-brand-50 hover:text-brand-700">Lộ trình 90 ngày</a>
            <a href="#hoc-phi" onclick="toggleMobileMenu()" class="block px-4 py-2.5 rounded-xl font-semibold text-slate-700 hover:bg-brand-50 hover:text-brand-700">Bảng học phí</a>
            <a href="#cam-nhan" onclick="toggleMobileMenu()" class="block px-4 py-2.5 rounded-xl font-semibold text-slate-700 hover:bg-brand-50 hover:text-brand-700">Cảm nhận học viên</a>
            <div class="pt-2">
                <a href="#dang-ky" onclick="toggleMobileMenu()" class="w-full bg-accent-500 hover:bg-accent-600 text-white font-heading font-bold text-center py-3.5 rounded-xl shadow-glow block">
                    Đăng ký ngay (Ưu đãi 40%)
                </a>
            </div>
        </div>
    </header>

    <!-- 2. HERO SECTION -->
    <section class="relative overflow-hidden bg-gradient-to-b from-brand-900 via-brand-800 to-brand-900 text-white py-14 sm:py-20 lg:py-24">
        <!-- Họa tiết trang trí nền -->
        <div class="absolute inset-0 opacity-10 pointer-events-none">
            <div class="absolute -top-24 -left-24 w-96 h-96 rounded-full bg-accent-500 blur-3xl"></div>
            <div class="absolute bottom-0 right-0 w-[32rem] h-[32rem] rounded-full bg-blue-400 blur-3xl"></div>
        </div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
                
                <!-- Cột trái: Nội dung chính -->
                <div class="lg:col-span-7 space-y-6 text-center lg:text-left">
                    <div class="inline-flex items-center gap-2 bg-white/10 backdrop-blur-sm border border-white/20 px-4 py-2 rounded-full text-xs sm:text-sm font-semibold text-amber-300">
                        <i class="fa-solid fa-star"></i>
                        <span>Phương pháp độc quyền tại TANDAT ENGLISH cho người mất gốc</span>
                    </div>

                    <h1 class="font-heading font-extrabold text-3xl sm:text-5xl lg:text-[50px] leading-[1.18] tracking-tight">
                        TANDAT ENGLISH - Xóa Mất Gốc, <span class="text-transparent bg-clip-text bg-gradient-to-r from-amber-300 via-orange-300 to-accent-500">Bật Phản Xạ</span> Sau 90 Ngày
                    </h1>

                    <p class="text-slate-200 text-base sm:text-lg leading-relaxed max-w-2xl mx-auto lg:mx-0">
                        Tạm biệt nỗi sợ tiếng Anh và cách học vẹt ngữ pháp khô khan! Làm chủ <strong>44 âm chuẩn IPA</strong>, nạp <strong>1.000 từ vựng thực chiến</strong> và phản xạ tự nhiên trong 12 tuần cùng giảng viên kèm sát 1-1 mỗi ngày.
                    </p>

                    <!-- Dual CTAs -->
                    <div class="flex flex-col sm:flex-row items-center justify-center lg:justify-start gap-4 pt-2">
                        <a href="#dang-ky" class="w-full sm:w-auto bg-accent-500 hover:bg-accent-600 text-white font-heading font-bold text-base px-8 py-4 rounded-2xl shadow-glow hover:-translate-y-0.5 transition-all flex items-center justify-center gap-3">
                            <span>Đăng ký học thử miễn phí</span>
                            <i class="fa-solid fa-paper-plane"></i>
                        </a>
                        <a href="#hoc-thu" onclick="switchDemoTab('quiz')" class="w-full sm:w-auto bg-white/10 hover:bg-white/20 text-white border border-white/25 font-heading font-bold text-base px-7 py-4 rounded-2xl transition-all flex items-center justify-center gap-2.5">
                            <i class="fa-solid fa-play-circle text-amber-300 text-lg"></i>
                            <span>Test trình độ nhanh</span>
                        </a>
                    </div>

                    <!-- Trust Badges / Stats -->
                    <div class="pt-6 border-t border-white/15 grid grid-cols-3 gap-4 text-left">
                        <div class="flex items-start gap-3">
                            <div class="w-10 h-10 rounded-xl bg-white/10 flex items-center justify-center text-amber-300 shrink-0 mt-0.5">
                                <i class="fa-solid fa-users"></i>
                            </div>
                            <div>
                                <div class="font-heading font-extrabold text-lg sm:text-2xl text-white">5,000+</div>
                                <div class="text-xs text-slate-300">Học viên xóa mất gốc</div>
                            </div>
                        </div>
                        <div class="flex items-start gap-3">
                            <div class="w-10 h-10 rounded-xl bg-white/10 flex items-center justify-center text-emerald-300 shrink-0 mt-0.5">
                                <i class="fa-solid fa-chalkboard-user"></i>
                            </div>
                            <div>
                                <div class="font-heading font-extrabold text-lg sm:text-2xl text-white">Kèm 1-1</div>
                                <div class="text-xs text-slate-300">Sửa phát âm mỗi ngày</div>
                            </div>
                        </div>
                        <div class="flex items-start gap-3">
                            <div class="w-10 h-10 rounded-xl bg-white/10 flex items-center justify-center text-orange-300 shrink-0 mt-0.5">
                                <i class="fa-solid fa-file-shield"></i>
                            </div>
                            <div>
                                <div class="font-heading font-extrabold text-lg sm:text-2xl text-white">Cam kết</div>
                                <div class="text-xs text-slate-300">Đầu ra bằng văn bản</div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Cột phải: Thẻ Mô Phỏng Học Tập Tương Tác -->
                <div class="lg:col-span-5">
                    <div class="bg-white text-slate-800 rounded-3xl p-6 sm:p-7 shadow-2xl border border-slate-100 relative">
                        <!-- Nhãn nổi -->
                        <div class="absolute -top-4 right-6 bg-emerald-500 text-white text-xs font-bold px-3.5 py-1.5 rounded-full shadow-md flex items-center gap-1.5">
                            <span class="w-2 h-2 rounded-full bg-white animate-ping"></span>
                            Trải nghiệm phát âm cùng TANDAT ENGLISH
                        </div>

                        <div class="flex items-center justify-between border-b border-slate-100 pb-4 mb-5">
                            <div class="flex items-center gap-3">
                                <div class="w-11 h-11 rounded-2xl bg-brand-50 text-brand-700 flex items-center justify-center font-bold text-lg">
                                    <i class="fa-solid fa-volume-high"></i>
                                </div>
                                <div>
                                    <span class="text-xs font-semibold text-slate-400 uppercase tracking-wider">Bài học mẫu tại TANDAT ENGLISH</span>
                                    <h3 class="font-heading font-bold text-slate-900 text-base">Chuẩn hóa âm /θ/ & Phản xạ câu</h3>
                                </div>
                            </div>
                            <span class="bg-brand-50 text-brand-700 font-bold text-xs px-2.5 py-1 rounded-lg">Ngày 01/90</span>
                        </div>

                        <!-- Hộp từ vựng mẫu có nút nghe thật -->
                        <div class="bg-slate-50 rounded-2xl p-5 border border-slate-200/70 mb-5">
                            <div class="flex items-center justify-between mb-2">
                                <div>
                                    <span class="text-xs font-bold text-accent-600 uppercase">Từ dễ phát âm sai #1</span>
                                    <div class="flex items-baseline gap-2.5 mt-1">
                                        <h4 class="font-heading font-extrabold text-2xl text-brand-900">Comfortable</h4>
                                        <span class="font-mono text-sm text-slate-500 bg-white px-2 py-0.5 rounded border border-slate-200">/ˈkʌm.fə.tə.bəl/</span>
                                    </div>
                                </div>
                                <button onclick="speakSampleText('Comfortable. I feel very comfortable speaking English today.')" class="w-12 h-12 rounded-2xl bg-brand-700 hover:bg-brand-800 text-white flex items-center justify-center shadow-md hover:scale-105 transition-all" title="Bấm để nghe phát âm chuẩn">
                                    <i class="fa-solid fa-volume-up text-lg"></i>
                                </button>
                            </div>
                            <p class="text-xs text-slate-600 mb-3">
                                <i class="fa-solid fa-circle-info text-brand-600 mr-1"></i>
                                <strong>Mẹo nhớ TANDAT ENGLISH:</strong> Chỉ đọc 3 âm tiết <em>"KUM-fơ-bồ"</em> (âm "table" ở cuối bị lược nhẹ, không đọc là "com-fo-tây-bồ").
                            </p>
                            <div class="bg-white rounded-xl p-3 border border-slate-200/80 text-sm">
                                <p class="font-semibold text-slate-800">"I feel very <span class="text-accent-600 underline">comfortable</span> speaking English today."</p>
                                <p class="text-xs text-slate-500 mt-0.5">→ Hôm nay tôi cảm thấy rất thoải mái khi nói tiếng Anh.</p>
                            </div>
                        </div>

                        <!-- Tiến độ mẫu 3 bước trong ngày -->
                        <div class="space-y-2.5 mb-5">
                            <div class="flex items-center justify-between text-xs font-semibold text-slate-600">
                                <span>Lộ trình 30 phút mỗi tối cho người bận rộn:</span>
                                <span class="text-emerald-600">Dễ áp dụng 100%</span>
                            </div>
                            <div class="grid grid-cols-3 gap-2 text-center text-xs">
                                <div class="bg-emerald-50 border border-emerald-200 text-emerald-800 p-2.5 rounded-xl font-medium">
                                    <i class="fa-solid fa-circle-check text-emerald-600 block mb-1 text-sm"></i>
                                    10p Phát âm IPA
                                </div>
                                <div class="bg-brand-50 border border-brand-200 text-brand-800 p-2.5 rounded-xl font-medium">
                                    <i class="fa-solid fa-bolt text-brand-600 block mb-1 text-sm"></i>
                                    10p Từ thực chiến
                                </div>
                                <div class="bg-orange-50 border border-orange-200 text-accent-700 p-2.5 rounded-xl font-medium">
                                    <i class="fa-solid fa-headset text-accent-600 block mb-1 text-sm"></i>
                                    10p Phản xạ 1-1
                                </div>
                            </div>
                        </div>

                        <div class="flex items-center justify-between bg-brand-900 text-white p-3.5 rounded-2xl text-xs">
                            <div class="flex items-center gap-2.5">
                                <div class="flex -space-x-2">
                                    <span class="w-7 h-7 rounded-full bg-amber-400 text-brand-900 font-bold flex items-center justify-center border-2 border-brand-900">T</span>
                                    <span class="w-7 h-7 rounded-full bg-emerald-400 text-brand-900 font-bold flex items-center justify-center border-2 border-brand-900">Đ</span>
                                    <span class="w-7 h-7 rounded-full bg-sky-400 text-brand-900 font-bold flex items-center justify-center border-2 border-brand-900">E</span>
                                </div>
                                <span><strong>Học viên TANDAT ENGLISH</strong> đang thực hành</span>
                            </div>
                            <a href="#hoc-thu" class="text-amber-300 font-bold hover:underline">Thử thêm →</a>
                        </div>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- 3. PAIN POINTS & SOLUTIONS (3-COLUMN GRID) -->
    <section id="loi-ich" class="py-16 sm:py-24 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Section Header -->
            <div class="text-center max-w-3xl mx-auto mb-14">
                <span class="text-accent-600 font-bold text-xs sm:text-sm uppercase tracking-wider bg-accent-50 px-3.5 py-1.5 rounded-full">
                    Phương pháp độc quyền tại TANDAT ENGLISH
                </span>
                <h2 class="font-heading font-extrabold text-2xl sm:text-4xl text-slate-900 mt-4 leading-tight">
                    Đập Tan 3 Rào Cản Lớn Nhất Của Người Mất Gốc Tiếng Anh
                </h2>
                <p class="text-slate-600 mt-3 text-base sm:text-lg">
                    Tại <strong>TANDAT ENGLISH</strong>, bạn không học thuộc lòng công thức khô khan mà đi theo đúng quy trình tự nhiên: <strong>Chuẩn hóa phát âm IPA → Nạp từ vựng thực chiến → Phản xạ giao tiếp 1-1</strong>.
                </p>
            </div>

            <!-- 3-Column Comparison Cards -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                
                <!-- Card 1 -->
                <div class="bg-slate-50 rounded-3xl p-7 border border-slate-200/80 shadow-soft hover:-translate-y-1 transition-all flex flex-col justify-between">
                    <div>
                        <!-- Nỗi đau -->
                        <div class="bg-rose-50 border border-rose-200/70 rounded-2xl p-4 mb-6">
                            <div class="flex items-center gap-2.5 text-rose-600 font-bold text-sm mb-1.5">
                                <i class="fa-solid fa-circle-xmark text-base"></i>
                                <span>Nỗi sợ #1: Sợ phát âm sai</span>
                            </div>
                            <p class="text-slate-600 text-sm">
                                Đọc tiếng Anh theo kiểu "Việt hóa", mất âm đuôi, nhấn sai trọng âm khiến người nước ngoài không hiểu và bản thân ngại mở lời.
                            </p>
                        </div>

                        <!-- Mũi tên chuyển đổi -->
                        <div class="flex items-center gap-3 my-4">
                            <div class="h-px bg-slate-200 flex-1"></div>
                            <span class="w-8 h-8 rounded-full bg-brand-700 text-white flex items-center justify-center text-xs shadow">
                                <i class="fa-solid fa-arrow-down"></i>
                            </span>
                            <div class="h-px bg-slate-200 flex-1"></div>
                        </div>

                        <!-- Giải pháp -->
                        <div class="mt-2">
                            <div class="w-12 h-12 rounded-2xl bg-brand-100 text-brand-700 flex items-center justify-center text-xl mb-4">
                                <i class="fa-solid fa-microphone-lines"></i>
                            </div>
                            <h3 class="font-heading font-bold text-xl text-slate-900 mb-2">
                                Chuẩn Hóa 44 Âm IPA Từ Gốc
                            </h3>
                            <p class="text-slate-600 text-sm leading-relaxed">
                                Hướng dẫn chi tiết vị trí môi, răng, lưỡi cho từng nguyên âm và phụ âm. Chỉnh sửa trực tiếp từng từ cho đến khi bạn tự đọc chuẩn bất kỳ từ mới nào trong từ điển.
                            </p>
                        </div>
                    </div>

                    <div class="mt-6 pt-4 border-t border-slate-200/80 flex items-center justify-between text-xs font-semibold text-brand-700">
                        <span>Hiệu quả ngay sau 4 tuần đầu</span>
                        <i class="fa-solid fa-check-double text-emerald-500 text-sm"></i>
                    </div>
                </div>

                <!-- Card 2 -->
                <div class="bg-slate-50 rounded-3xl p-7 border border-slate-200/80 shadow-soft hover:-translate-y-1 transition-all flex flex-col justify-between">
                    <div>
                        <!-- Nỗi đau -->
                        <div class="bg-rose-50 border border-rose-200/70 rounded-2xl p-4 mb-6">
                            <div class="flex items-center gap-2.5 text-rose-600 font-bold text-sm mb-1.5">
                                <i class="fa-solid fa-circle-xmark text-base"></i>
                                <span>Nỗi sợ #2: Học trước quên sau</span>
                            </div>
                            <p class="text-slate-600 text-sm">
                                Học từ vựng rời rạc trên giấy, khi cần nói lại đứng dịch từng chữ từ tiếng Việt sang tiếng Anh nên ấp úng, không ghép thành câu trọn vẹn.
                            </p>
                        </div>

                        <!-- Mũi tên chuyển đổi -->
                        <div class="flex items-center gap-3 my-4">
                            <div class="h-px bg-slate-200 flex-1"></div>
                            <span class="w-8 h-8 rounded-full bg-brand-700 text-white flex items-center justify-center text-xs shadow">
                                <i class="fa-solid fa-arrow-down"></i>
                            </span>
                            <div class="h-px bg-slate-200 flex-1"></div>
                        </div>

                        <!-- Giải pháp -->
                        <div class="mt-2">
                            <div class="w-12 h-12 rounded-2xl bg-amber-100 text-accent-600 flex items-center justify-center text-xl mb-4">
                                <i class="fa-solid fa-brain"></i>
                            </div>
                            <h3 class="font-heading font-bold text-xl text-slate-900 mb-2">
                                Phản Xạ Spaced Repetition
                            </h3>
                            <p class="text-slate-600 text-sm leading-relaxed">
                                Nạp từ vựng theo <strong>cụm từ (Chunks)</strong> gắn liền với ngữ cảnh thực tế kết hợp thuật toán lặp lại ngắt quãng, giúp nhớ sâu gấp 5 lần mà không cần chép phạt.
                            </p>
                        </div>
                    </div>

                    <div class="mt-6 pt-4 border-t border-slate-200/80 flex items-center justify-between text-xs font-semibold text-brand-700">
                        <span>Nắm chắc 1.000+ từ thông dụng</span>
                        <i class="fa-solid fa-check-double text-emerald-500 text-sm"></i>
                    </div>
                </div>

                <!-- Card 3 -->
                <div class="bg-slate-50 rounded-3xl p-7 border border-slate-200/80 shadow-soft hover:-translate-y-1 transition-all flex flex-col justify-between">
                    <div>
                        <!-- Nỗi đau -->
                        <div class="bg-rose-50 border border-rose-200/70 rounded-2xl p-4 mb-6">
                            <div class="flex items-center gap-2.5 text-rose-600 font-bold text-sm mb-1.5">
                                <i class="fa-solid fa-circle-xmark text-base"></i>
                                <span>Nỗi sợ #3: Nghe như "vịt nghe sấm"</span>
                            </div>
                            <p class="text-slate-600 text-sm">
                                Nhìn mặt chữ thì biết nghĩa nhưng khi người bản xứ nói nhanh, nối âm hoặc nuốt âm là hoàn toàn không bắt kịp từ khóa.
                            </p>
                        </div>

                        <!-- Mũi tên chuyển đổi -->
                        <div class="flex items-center gap-3 my-4">
                            <div class="h-px bg-slate-200 flex-1"></div>
                            <span class="w-8 h-8 rounded-full bg-brand-700 text-white flex items-center justify-center text-xs shadow">
                                <i class="fa-solid fa-arrow-down"></i>
                            </span>
                            <div class="h-px bg-slate-200 flex-1"></div>
                        </div>

                        <!-- Giải pháp -->
                        <div class="mt-2">
                            <div class="w-12 h-12 rounded-2xl bg-emerald-100 text-emerald-600 flex items-center justify-center text-xl mb-4">
                                <i class="fa-solid fa-comments"></i>
                            </div>
                            <h3 class="font-heading font-bold text-xl text-slate-900 mb-2">
                                Thực Hành Phản Xạ 1-1 Mỗi Ngày
                            </h3>
                            <p class="text-slate-600 text-sm leading-relaxed">
                                Luyện nghe bắt từ khóa kết hợp đóng vai (Role-play) 36 tình huống giao tiếp đời sống & công việc cùng giảng viên và trợ giảng 1-1.
                            </p>
                        </div>
                    </div>

                    <div class="mt-6 pt-4 border-t border-slate-200/80 flex items-center justify-between text-xs font-semibold text-brand-700">
                        <span>Tự tin mở lời sau 90 ngày</span>
                        <i class="fa-solid fa-check-double text-emerald-500 text-sm"></i>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- 4. INTERACTIVE CURRICULUM TIMELINE (LỘ TRÌNH 3 GIAI ĐOẠN) -->
    <section id="lo-trinh" class="py-16 sm:py-24 bg-slate-100/80 border-y border-slate-200/70">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-12">
                <span class="text-brand-700 font-bold text-xs sm:text-sm uppercase tracking-wider bg-brand-100 px-3.5 py-1.5 rounded-full">
                    Lộ trình 90 ngày tại TANDAT ENGLISH
                </span>
                <h2 class="font-heading font-extrabold text-2xl sm:text-4xl text-slate-900 mt-4">
                    Lộ Trình 3 Giai Đoạn Từ Con Số 0 Đến Giao Tiếp Tự Tin
                </h2>
                <p class="text-slate-600 mt-3 text-base">
                    Bấm vào từng giai đoạn bên dưới để khám phá chi tiết nội dung học, lịch trình hàng tuần và kết quả đầu ra tại <strong>TANDAT ENGLISH</strong>.
                </p>
            </div>

            <!-- Nút chuyển đổi 3 giai đoạn (Timeline Tabs) -->
            <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-8">
                <button onclick="selectStage(1)" id="stage-btn-1" class="stage-btn text-left p-5 rounded-2xl border-2 transition-all bg-brand-900 text-white border-brand-900 shadow-lg">
                    <div class="flex items-center justify-between mb-2">
                        <span class="text-xs font-bold uppercase tracking-wider px-2.5 py-1 rounded-md bg-accent-500 text-white">Giai đoạn 1 • Tuần 1 - 4</span>
                        <i class="fa-solid fa-volume-high text-xl text-amber-300"></i>
                    </div>
                    <h3 class="font-heading font-bold text-lg">Phá Băng & Chuẩn Hóa Âm IPA</h3>
                    <p class="text-xs text-slate-200 mt-1">Làm chủ 44 âm IPA, xây nền tảng nghe - đọc chuẩn xác</p>
                </button>

                <button onclick="selectStage(2)" id="stage-btn-2" class="stage-btn text-left p-5 rounded-2xl border-2 transition-all bg-white text-slate-800 border-slate-200 hover:border-brand-400">
                    <div class="flex items-center justify-between mb-2">
                        <span class="text-xs font-bold uppercase tracking-wider px-2.5 py-1 rounded-md bg-brand-100 text-brand-800">Giai đoạn 2 • Tuần 5 - 8</span>
                        <i class="fa-solid fa-layer-group text-xl text-brand-600"></i>
                    </div>
                    <h3 class="font-heading font-bold text-lg">Xây Nền Từ Vựng & Phản Xạ Câu</h3>
                    <p class="text-xs text-slate-500 mt-1">Nạp 1.000 từ thực chiến, bỏ thói quen dịch từng chữ trong đầu</p>
                </button>

                <button onclick="selectStage(3)" id="stage-btn-3" class="stage-btn text-left p-5 rounded-2xl border-2 transition-all bg-white text-slate-800 border-slate-200 hover:border-brand-400">
                    <div class="flex items-center justify-between mb-2">
                        <span class="text-xs font-bold uppercase tracking-wider px-2.5 py-1 rounded-md bg-brand-100 text-brand-800">Giai đoạn 3 • Tuần 9 - 12</span>
                        <i class="fa-solid fa-comments text-xl text-brand-600"></i>
                    </div>
                    <h3 class="font-heading font-bold text-lg">Giao Tiếp Thực Chiến & Thuyết Trình Tự Tin</h3>
                    <p class="text-xs text-slate-500 mt-1">Thực hành phản xạ đối thoại công việc, du lịch & đời sống</p>
                </button>
            </div>

            <!-- Khung hiển thị chi tiết từng giai đoạn (Dynamic Panel) -->
            <div id="stage-content-panel" class="bg-white rounded-3xl p-6 sm:p-10 shadow-soft border border-slate-200/80 transition-all">
                <!-- Nội dung được render tự động bởi JavaScript -->
            </div>
        </div>
    </section>

    <!-- 5. INTERACTIVE MINI DEMO ("TRẢI NGHIỆM HỌC THỬ CÙNG TANDAT ENGLISH") -->
    <section id="hoc-thu" class="py-16 sm:py-24 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center max-w-3xl mx-auto mb-10">
                <span class="text-emerald-700 font-bold text-xs sm:text-sm uppercase tracking-wider bg-emerald-100 px-3.5 py-1.5 rounded-full">
                    Tương tác trực tiếp ngay trên web
                </span>
                <h2 class="font-heading font-extrabold text-2xl sm:text-4xl text-slate-900 mt-4">
                    Trải Nghiệm Học Thử Cùng TANDAT ENGLISH
                </h2>
                <p class="text-slate-600 mt-3">
                    Hãy tự mình trải nghiệm Flashcard 3D tích hợp phát âm chuẩn của <strong>TANDAT ENGLISH</strong> hoặc làm bài kiểm tra 3 câu để nhận gợi ý khóa học phù hợp nhất.
                </p>
            </div>

            <!-- Nút chuyển Tab Học thử / Bài Test -->
            <div class="flex justify-center mb-10">
                <div class="inline-flex bg-slate-100 p-1.5 rounded-2xl border border-slate-200">
                    <button onclick="switchDemoTab('flashcard')" id="tab-btn-flashcard" class="px-5 py-3 rounded-xl font-heading font-bold text-sm transition-all bg-brand-800 text-white shadow">
                        <i class="fa-solid fa-volume-high mr-2"></i>1. Học thử Flashcard Phát Âm
                    </button>
                    <button onclick="switchDemoTab('quiz')" id="tab-btn-quiz" class="px-5 py-3 rounded-xl font-heading font-bold text-sm transition-all text-slate-600 hover:text-slate-900">
                        <i class="fa-solid fa-clipboard-check mr-2"></i>2. Bài Test Trình Độ (1 Phút)
                    </button>
                </div>
            </div>

            <!-- TAB 1: INTERACTIVE FLIP FLASHCARDS WITH WEB SPEECH API -->
            <div id="demo-tab-flashcard" class="space-y-6">
                <div class="bg-brand-50 border border-brand-200/80 rounded-2xl p-4 flex flex-col sm:flex-row items-center justify-between gap-4 text-sm text-brand-900">
                    <div class="flex items-center gap-3">
                        <span class="w-9 h-9 rounded-xl bg-brand-700 text-white flex items-center justify-center shrink-0">
                            <i class="fa-solid fa-hand-pointer"></i>
                        </span>
                        <span><strong>Hướng dẫn:</strong> Bấm nút <strong>"Nghe chuẩn"</strong> để nghe giọng đọc bản xứ hoặc <strong>"Lật xem mẹo"</strong> để xem bí quyết phát âm của TANDAT ENGLISH!</span>
                    </div>
                    <span id="speech-status" class="text-xs font-semibold bg-white px-3 py-1.5 rounded-lg border border-brand-200 shrink-0">
                        <i class="fa-solid fa-circle-check text-emerald-500 mr-1"></i> Âm thanh sẵn sàng
                    </span>
                </div>

                <!-- Grid 4 Flashcards -->
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
                    
                    <!-- Flashcard 1 -->
                    <div class="perspective-1000 h-80">
                        <div id="card-1" class="transform-style-3d relative w-full h-full rounded-3xl shadow-soft border border-slate-200 bg-white">
                            <!-- Mặt trước -->
                            <div class="backface-hidden absolute inset-0 p-6 flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold bg-rose-100 text-rose-700 px-2.5 py-1 rounded-full">Hay đọc sai #1</span>
                                    <span class="text-xs font-mono text-slate-400">IPA /wenz.deɪ/</span>
                                </div>
                                <div class="text-center my-auto">
                                    <h3 class="font-heading font-extrabold text-3xl text-brand-900 mb-1">Wednesday</h3>
                                    <p class="text-sm text-slate-500 font-medium">Thứ Tư</p>
                                    <p class="text-xs text-rose-500 mt-3 line-through">Hay đọc nhầm: "Quét-nét-đây"</p>
                                </div>
                                <div class="grid grid-cols-2 gap-2">
                                    <button onclick="speakSampleText('Wednesday. Lets have a meeting on Wednesday.')" class="bg-brand-700 hover:bg-brand-800 text-white text-xs font-bold py-2.5 px-3 rounded-xl flex items-center justify-center gap-1.5 transition">
                                        <i class="fa-solid fa-volume-high"></i> Nghe chuẩn
                                    </button>
                                    <button onclick="flipCard('card-1')" class="bg-slate-100 hover:bg-slate-200 text-slate-700 text-xs font-bold py-2.5 px-3 rounded-xl flex items-center justify-center gap-1.5 transition">
                                        <i class="fa-solid fa-rotate"></i> Lật xem mẹo
                                    </button>
                                </div>
                            </div>
                            <!-- Mặt sau -->
                            <div class="backface-hidden rotate-y-180 absolute inset-0 p-6 bg-brand-900 text-white rounded-3xl flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold text-amber-300 uppercase">Bí quyết phát âm</span>
                                    <button onclick="flipCard('card-1')" class="text-white/70 hover:text-white text-sm"><i class="fa-solid fa-xmark"></i></button>
                                </div>
                                <div class="space-y-3 text-sm">
                                    <p><strong class="text-amber-300">Âm câm:</strong> Chữ <strong>"d"</strong> ở giữa bị câm hoàn toàn. Chỉ đọc gọn 2 âm tiết là <strong>"WENZ-day"</strong>.</p>
                                    <div class="bg-white/10 p-3 rounded-xl text-xs">
                                        <p class="font-semibold text-white">"Let's have a meeting on Wednesday."</p>
                                        <p class="text-slate-300 mt-1">Hãy họp vào thứ Tư nhé.</p>
                                    </div>
                                </div>
                                <button onclick="flipCard('card-1')" class="w-full bg-white/15 hover:bg-white/25 text-white text-xs font-bold py-2.5 rounded-xl transition">
                                    Quay lại mặt trước
                                </button>
                            </div>
                        </div>
                    </div>

                    <!-- Flashcard 2 -->
                    <div class="perspective-1000 h-80">
                        <div id="card-2" class="transform-style-3d relative w-full h-full rounded-3xl shadow-soft border border-slate-200 bg-white">
                            <!-- Mặt trước -->
                            <div class="backface-hidden absolute inset-0 p-6 flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold bg-rose-100 text-rose-700 px-2.5 py-1 rounded-full">Hay đọc sai #2</span>
                                    <span class="text-xs font-mono text-slate-400">IPA /ˈvedʒ.tə.bəl/</span>
                                </div>
                                <div class="text-center my-auto">
                                    <h3 class="font-heading font-extrabold text-3xl text-brand-900 mb-1">Vegetable</h3>
                                    <p class="text-sm text-slate-500 font-medium">Rau củ</p>
                                    <p class="text-xs text-rose-500 mt-3 line-through">Hay đọc nhầm: "Ve-ge-tây-bồ"</p>
                                </div>
                                <div class="grid grid-cols-2 gap-2">
                                    <button onclick="speakSampleText('Vegetable. Fresh vegetables are good for your health.')" class="bg-brand-700 hover:bg-brand-800 text-white text-xs font-bold py-2.5 px-3 rounded-xl flex items-center justify-center gap-1.5 transition">
                                        <i class="fa-solid fa-volume-high"></i> Nghe chuẩn
                                    </button>
                                    <button onclick="flipCard('card-2')" class="bg-slate-100 hover:bg-slate-200 text-slate-700 text-xs font-bold py-2.5 px-3 rounded-xl flex items-center justify-center gap-1.5 transition">
                                        <i class="fa-solid fa-rotate"></i> Lật xem mẹo
                                    </button>
                                </div>
                            </div>
                            <!-- Mặt sau -->
                            <div class="backface-hidden rotate-y-180 absolute inset-0 p-6 bg-brand-900 text-white rounded-3xl flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold text-amber-300 uppercase">Bí quyết phát âm</span>
                                    <button onclick="flipCard('card-2')" class="text-white/70 hover:text-white text-sm"><i class="fa-solid fa-xmark"></i></button>
                                </div>
                                <div class="space-y-3 text-sm">
                                    <p><strong class="text-amber-300">Lược âm:</strong> Chữ <strong>"e"</strong> thứ hai bị câm. Từ này chỉ có 3 âm tiết: <strong>"VEDJ-tơ-bồ"</strong>.</p>
                                    <div class="bg-white/10 p-3 rounded-xl text-xs">
                                        <p class="font-semibold text-white">"Fresh vegetables are good for your health."</p>
                                        <p class="text-slate-300 mt-1">Rau củ tươi rất tốt cho sức khỏe của bạn.</p>
                                    </div>
                                </div>
                                <button onclick="flipCard('card-2')" class="w-full bg-white/15 hover:bg-white/25 text-white text-xs font-bold py-2.5 rounded-xl transition">
                                    Quay lại mặt trước
                                </button>
                            </div>
                        </div>
                    </div>

                    <!-- Flashcard 3 -->
                    <div class="perspective-1000 h-80">
                        <div id="card-3" class="transform-style-3d relative w-full h-full rounded-3xl shadow-soft border border-slate-200 bg-white">
                            <!-- Mặt trước -->
                            <div class="backface-hidden absolute inset-0 p-6 flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold bg-rose-100 text-rose-700 px-2.5 py-1 rounded-full">Hay đọc sai #3</span>
                                    <span class="text-xs font-mono text-slate-400">IPA /ˈʃed.juːl/</span>
                                </div>
                                <div class="text-center my-auto">
                                    <h3 class="font-heading font-extrabold text-3xl text-brand-900 mb-1">Schedule</h3>
                                    <p class="text-sm text-slate-500 font-medium">Lịch trình</p>
                                    <p class="text-xs text-rose-500 mt-3 line-through">Hay đọc nhầm: "Sờ-che-đun"</p>
                                </div>
                                <div class="grid grid-cols-2 gap-2">
                                    <button onclick="speakSampleText('Schedule. Let me check my schedule for tomorrow.')" class="bg-brand-700 hover:bg-brand-800 text-white text-xs font-bold py-2.5 px-3 rounded-xl flex items-center justify-center gap-1.5 transition">
                                        <i class="fa-solid fa-volume-high"></i> Nghe chuẩn
                                    </button>
                                    <button onclick="flipCard('card-3')" class="bg-slate-100 hover:bg-slate-200 text-slate-700 text-xs font-bold py-2.5 px-3 rounded-xl flex items-center justify-center gap-1.5 transition">
                                        <i class="fa-solid fa-rotate"></i> Lật xem mẹo
                                    </button>
                                </div>
                            </div>
                            <!-- Mặt sau -->
                            <div class="backface-hidden rotate-y-180 absolute inset-0 p-6 bg-brand-900 text-white rounded-3xl flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold text-amber-300 uppercase">Bí quyết phát âm</span>
                                    <button onclick="flipCard('card-3')" class="text-white/70 hover:text-white text-sm"><i class="fa-solid fa-xmark"></i></button>
                                </div>
                                <div class="space-y-3 text-sm">
                                    <p><strong class="text-amber-300">Anh - Mỹ:</strong> Đọc cụm đầu là <strong>"SKED-ju-ồ"</strong>. Tuyệt đối không tách âm /s/ rời ra thành "sờ".</p>
                                    <div class="bg-white/10 p-3 rounded-xl text-xs">
                                        <p class="font-semibold text-white">"Let me check my schedule for tomorrow."</p>
                                        <p class="text-slate-300 mt-1">Để tôi kiểm tra lịch trình ngày mai nhé.</p>
                                    </div>
                                </div>
                                <button onclick="flipCard('card-3')" class="w-full bg-white/15 hover:bg-white/25 text-white text-xs font-bold py-2.5 rounded-xl transition">
                                    Quay lại mặt trước
                                </button>
                            </div>
                        </div>
                    </div>

                    <!-- Flashcard 4 -->
                    <div class="perspective-1000 h-80">
                        <div id="card-4" class="transform-style-3d relative w-full h-full rounded-3xl shadow-soft border border-slate-200 bg-white">
                            <!-- Mặt trước -->
                            <div class="backface-hidden absolute inset-0 p-6 flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold bg-rose-100 text-rose-700 px-2.5 py-1 rounded-full">Hay đọc sai #4</span>
                                    <span class="text-xs font-mono text-slate-400">IPA /rɪˈsiːt/</span>
                                </div>
                                <div class="text-center my-auto">
                                    <h3 class="font-heading font-extrabold text-3xl text-brand-900 mb-1">Receipt</h3>
                                    <p class="text-sm text-slate-500 font-medium">Hóa đơn / Biên lai</p>
                                    <p class="text-xs text-rose-500 mt-3 line-through">Hay đọc nhầm: "Ri-xếp-tờ"</p>
                                </div>
                                <div class="grid grid-cols-2 gap-2">
                                    <button onclick="speakSampleText('Receipt. Could I have the receipt, please?')" class="bg-brand-700 hover:bg-brand-800 text-white text-xs font-bold py-2.5 px-3 rounded-xl flex items-center justify-center gap-1.5 transition">
                                        <i class="fa-solid fa-volume-high"></i> Nghe chuẩn
                                    </button>
                                    <button onclick="flipCard('card-4')" class="bg-slate-100 hover:bg-slate-200 text-slate-700 text-xs font-bold py-2.5 px-3 rounded-xl flex items-center justify-center gap-1.5 transition">
                                        <i class="fa-solid fa-rotate"></i> Lật xem mẹo
                                    </button>
                                </div>
                            </div>
                            <!-- Mặt sau -->
                            <div class="backface-hidden rotate-y-180 absolute inset-0 p-6 bg-brand-900 text-white rounded-3xl flex flex-col justify-between">
                                <div class="flex items-center justify-between">
                                    <span class="text-xs font-bold text-amber-300 uppercase">Bí quyết phát âm</span>
                                    <button onclick="flipCard('card-4')" class="text-white/70 hover:text-white text-sm"><i class="fa-solid fa-xmark"></i></button>
                                </div>
                                <div class="space-y-3 text-sm">
                                    <p><strong class="text-amber-300">Âm câm:</strong> Chữ <strong>"p"</strong> ở gần cuối bị câm hoàn toàn. Đọc kéo dài âm /i:/ thành <strong>"rì-SI:T"</strong>.</p>
                                    <div class="bg-white/10 p-3 rounded-xl text-xs">
                                        <p class="font-semibold text-white">"Could I have the receipt, please?"</p>
                                        <p class="text-slate-300 mt-1">Cho tôi xin hóa đơn được không ạ?</p>
                                    </div>
                                </div>
                                <button onclick="flipCard('card-4')" class="w-full bg-white/15 hover:bg-white/25 text-white text-xs font-bold py-2.5 rounded-xl transition">
                                    Quay lại mặt trước
                                </button>
                            </div>
                        </div>
                    </div>

                </div>
            </div>

            <!-- TAB 2: INTERACTIVE 3-QUESTION PLACEMENT QUIZ -->
            <div id="demo-tab-quiz" class="hidden max-w-3xl mx-auto">
                <div class="bg-slate-50 rounded-3xl p-6 sm:p-10 border border-slate-200 shadow-soft">
                    <div id="quiz-container">
                        <!-- Nội dung câu hỏi được render động bởi JS -->
                    </div>
                </div>
            </div>

        </div>
    </section>

    <!-- 6. PRICING TABLE (3 TIERS AT TANDAT ENGLISH) -->
    <section id="hoc-phi" class="py-16 sm:py-24 bg-slate-900 text-white relative overflow-hidden">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="text-center max-w-3xl mx-auto mb-14">
                <span class="text-amber-300 font-bold text-xs sm:text-sm uppercase tracking-wider bg-white/10 px-3.5 py-1.5 rounded-full">
                    Đầu tư 1 lần - Tự tin giao tiếp trọn đời cùng TANDAT ENGLISH
                </span>
                <h2 class="font-heading font-extrabold text-2xl sm:text-4xl mt-4">
                    Bảng Học Phí & Chương Trình Học Bổng 40%
                </h2>
                <p class="text-slate-300 mt-3">
                    Cam kết minh bạch chi phí tại <strong>TANDAT ENGLISH</strong>, tặng kèm bộ quà tặng độc quyền và hỗ trợ chia nhỏ học phí 0% lãi suất.
                </p>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 items-stretch">
                
                <!-- Tier 1: Gói Cơ Bản -->
                <div class="bg-slate-800/90 border border-slate-700 rounded-3xl p-8 flex flex-col justify-between hover:border-slate-500 transition-all">
                    <div>
                        <div class="flex items-center justify-between mb-4">
                            <span class="text-xs font-bold uppercase tracking-wider text-slate-300 bg-slate-700 px-3 py-1 rounded-full">Gói Cơ Bản</span>
                            <span class="text-xs text-slate-400">6 Tuần</span>
                        </div>
                        <h3 class="font-heading font-extrabold text-2xl text-white">Gói Cơ Bản (Lấy Lại Gốc)</h3>
                        <p class="text-slate-400 text-sm mt-2">Phù hợp cho người mới bắt đầu muốn chuẩn hóa phát âm IPA và nắm vững từ vựng nền tảng.</p>

                        <div class="my-6 pt-6 border-t border-slate-700">
                            <div class="text-sm text-slate-400 line-through">Học phí gốc: 3.200.000đ</div>
                            <div class="flex items-baseline gap-2 mt-1">
                                <span class="font-heading font-extrabold text-4xl text-white">1.890.000đ</span>
                                <span class="text-xs text-slate-400">/ trọn khóa</span>
                            </div>
                        </div>

                        <ul class="space-y-3.5 text-sm text-slate-200 mb-8">
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-emerald-400 mt-1"></i>
                                <span>Chuẩn hóa trọn bộ <strong>44 âm IPA</strong> chuẩn quốc tế</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-emerald-400 mt-1"></i>
                                <span>Nạp <strong>500 từ vựng</strong> & cụm câu thông dụng nhất</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-emerald-400 mt-1"></i>
                                <span>Lớp học nhóm nhỏ tương tác trực tiếp</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-emerald-400 mt-1"></i>
                                <span>Trợ giảng TANDAT ENGLISH chấm chữa bài mỗi ngày</span>
                            </li>
                        </ul>
                    </div>

                    <button onclick="selectPackageAndScroll('Gói Cơ Bản (1.890.000đ)')" class="w-full bg-white/10 hover:bg-white/20 text-white font-heading font-bold py-4 rounded-2xl border border-white/20 transition-all">
                        Chọn Gói Cơ Bản
                    </button>
                </div>

                <!-- Tier 2: Gói Tiêu Chuẩn - Bán chạy nhất -->
                <div class="bg-gradient-to-b from-brand-700 to-brand-900 border-2 border-accent-500 rounded-3xl p-8 flex flex-col justify-between shadow-2xl relative lg:-translate-y-4">
                    <div class="absolute -top-4 left-1/2 -translate-x-1/2 bg-accent-500 text-white font-heading font-bold text-xs uppercase tracking-wider px-4 py-1.5 rounded-full shadow-lg flex items-center gap-1.5 whitespace-nowrap">
                        <i class="fa-solid fa-fire"></i> Bán chạy nhất tại TANDAT ENGLISH
                    </div>

                    <div>
                        <div class="flex items-center justify-between mb-4 mt-2">
                            <span class="text-xs font-bold uppercase tracking-wider text-amber-300 bg-white/10 px-3 py-1 rounded-full">Gói Tiêu Chuẩn</span>
                            <span class="text-xs text-amber-200 font-semibold">Trọn lộ trình 12 Tuần</span>
                        </div>
                        <h3 class="font-heading font-extrabold text-2xl text-white">Gói Tiêu Chuẩn Toàn Diện</h3>
                        <p class="text-blue-100 text-sm mt-2">Đi trọn lộ trình 3 giai đoạn từ mất gốc hoàn toàn đến tự tin phản xạ giao tiếp & thuyết trình.</p>

                        <div class="my-6 pt-6 border-t border-white/15">
                            <div class="text-sm text-blue-200 line-through">Học phí gốc: 5.800.000đ</div>
                            <div class="flex items-baseline gap-2 mt-1">
                                <span class="font-heading font-extrabold text-4xl text-amber-300">3.490.000đ</span>
                                <span class="text-xs text-blue-100">/ trọn khóa 90 ngày</span>
                            </div>
                        </div>

                        <ul class="space-y-3.5 text-sm text-white mb-8">
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-amber-300 mt-1"></i>
                                <span><strong>Trọn bộ 3 Giai Đoạn:</strong> Phá băng IPA + 1.000 Từ vựng + 36 Tình huống thực chiến</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-amber-300 mt-1"></i>
                                <span><strong>24 buổi thực hành Phản xạ 1-1</strong> cùng đội ngũ TANDAT ENGLISH</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-amber-300 mt-1"></i>
                                <span>Tặng Bộ Flashcard 1.000 từ & Kho bài nghe trọn đời</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-amber-300 mt-1"></i>
                                <span><strong>Cam kết đầu ra bằng văn bản</strong> - Học lại miễn phí nếu chưa đạt</span>
                            </li>
                        </ul>
                    </div>

                    <button onclick="selectPackageAndScroll('Gói Tiêu Chuẩn - Bán chạy nhất (3.490.000đ)')" class="w-full bg-accent-500 hover:bg-accent-600 text-white font-heading font-bold py-4 rounded-2xl shadow-glow transition-all">
                        Chọn Gói Tiêu Chuẩn →
                    </button>
                </div>

                <!-- Tier 3: Gói VIP Kèm 1-1 -->
                <div class="bg-slate-800/90 border border-slate-700 rounded-3xl p-8 flex flex-col justify-between hover:border-slate-500 transition-all">
                    <div>
                        <div class="flex items-center justify-between mb-4">
                            <span class="text-xs font-bold uppercase tracking-wider text-amber-300 bg-amber-500/20 px-3 py-1 rounded-full">Gói VIP Kèm 1-1</span>
                            <span class="text-xs text-slate-400">Linh hoạt 8 - 12 Tuần</span>
                        </div>
                        <h3 class="font-heading font-extrabold text-2xl text-white">Gói VIP Kèm 1-1 Cá Nhân Hóa</h3>
                        <p class="text-slate-400 text-sm mt-2">Dành cho người đi làm bận rộn, cần lịch học linh hoạt hoặc cần gấp tiếng Anh phỏng vấn, công việc.</p>

                        <div class="my-6 pt-6 border-t border-slate-700">
                            <div class="text-sm text-slate-400 line-through">Học phí gốc: 9.500.000đ</div>
                            <div class="flex items-baseline gap-2 mt-1">
                                <span class="font-heading font-extrabold text-4xl text-white">5.690.000đ</span>
                                <span class="text-xs text-slate-400">/ trọn khóa VIP</span>
                            </div>
                        </div>

                        <ul class="space-y-3.5 text-sm text-slate-200 mb-8">
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-emerald-400 mt-1"></i>
                                <span><strong>1 Giảng viên TANDAT ENGLISH kèm 1 Học viên</strong> xuyên suốt</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-emerald-400 mt-1"></i>
                                <span>Chủ động chọn khung giờ học (7h00 - 22h30 mỗi ngày)</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-emerald-400 mt-1"></i>
                                <span>Thiết kế giáo trình riêng theo đúng ngành nghề của bạn</span>
                            </li>
                            <li class="flex items-start gap-3">
                                <i class="fa-solid fa-circle-check text-emerald-400 mt-1"></i>
                                <span>Luyện phỏng vấn CV, thuyết trình & viết Email công sở</span>
                            </li>
                        </ul>
                    </div>

                    <button onclick="selectPackageAndScroll('Gói VIP Kèm 1-1 (5.690.000đ)')" class="w-full bg-white/10 hover:bg-white/20 text-white font-heading font-bold py-4 rounded-2xl border border-white/20 transition-all">
                        Chọn Gói VIP Kèm 1-1
                    </button>
                </div>

            </div>
        </div>
    </section>

    <!-- 7. STUDENT TESTIMONIALS & INTERACTIVE FAQ ACCORDION -->
    <section id="cam-nhan" class="py-16 sm:py-24 bg-white">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            
            <!-- Phần Đánh giá học viên -->
            <div class="text-center max-w-3xl mx-auto mb-14">
                <span class="text-brand-700 font-bold text-xs sm:text-sm uppercase tracking-wider bg-brand-50 px-3.5 py-1.5 rounded-full">
                    Niềm tự hào của TANDAT ENGLISH
                </span>
                <h2 class="font-heading font-extrabold text-2xl sm:text-4xl text-slate-900 mt-4">
                    Hơn 5.000 Học Viên Đã Xóa Mất Gốc Tại TANDAT ENGLISH
                </h2>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mb-20">
                <!-- Review 1 -->
                <div class="bg-slate-50 rounded-3xl p-7 border border-slate-200/80 shadow-soft flex flex-col justify-between">
                    <div>
                        <div class="flex items-center gap-1 text-amber-400 text-sm mb-4">
                            <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                        </div>
                        <p class="text-slate-700 text-sm leading-relaxed italic">
                            "Trước khi biết đến TANDAT ENGLISH mình mất gốc suốt nhiều năm, nhìn chữ tiếng Anh là ngại đọc. Nhờ 4 tuần đầu phá băng chỉnh từng âm IPA tận tình mà giờ mình nhìn phiên âm tự đọc chuẩn được luôn, đi phỏng vấn tự tin hẳn!"
                        </p>
                    </div>
                    <div class="flex items-center gap-3.5 mt-6 pt-4 border-t border-slate-200">
                        <div class="w-11 h-11 rounded-full bg-brand-700 text-white font-heading font-bold flex items-center justify-center">
                            M
                        </div>
                        <div>
                            <h4 class="font-heading font-bold text-slate-900 text-sm">Bạn Nguyễn Minh Thư</h4>
                            <p class="text-xs text-slate-500">Sinh viên năm cuối • Học viên Gói Tiêu Chuẩn</p>
                        </div>
                    </div>
                </div>

                <!-- Review 2 -->
                <div class="bg-slate-50 rounded-3xl p-7 border border-slate-200/80 shadow-soft flex flex-col justify-between">
                    <div>
                        <div class="flex items-center gap-1 text-amber-400 text-sm mb-4">
                            <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                        </div>
                        <p class="text-slate-700 text-sm leading-relaxed italic">
                            "Mình đi làm kỹ thuật bận rộn nên rất sợ học lý thuyết dài dòng. Lộ trình của TANDAT ENGLISH nạp cụm từ thực chiến và luyện phản xạ 1-1 mỗi tối 30 phút cực kỳ hợp với người đi làm. Sau 3 tháng mình đã tự giao tiếp với đối tác được."
                        </p>
                    </div>
                    <div class="flex items-center gap-3.5 mt-6 pt-4 border-t border-slate-200">
                        <div class="w-11 h-11 rounded-full bg-accent-500 text-white font-heading font-bold flex items-center justify-center">
                            H
                        </div>
                        <div>
                            <h4 class="font-heading font-bold text-slate-900 text-sm">Anh Trần Hoàng Nam</h4>
                            <p class="text-xs text-slate-500">Kỹ sư phần mềm • Học viên Gói VIP Kèm 1-1</p>
                        </div>
                    </div>
                </div>

                <!-- Review 3 -->
                <div class="bg-slate-50 rounded-3xl p-7 border border-slate-200/80 shadow-soft flex flex-col justify-between">
                    <div>
                        <div class="flex items-center gap-1 text-amber-400 text-sm mb-4">
                            <i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i><i class="fa-solid fa-star"></i>
                        </div>
                        <p class="text-slate-700 text-sm leading-relaxed italic">
                            "Ấn tượng nhất ở TANDAT ENGLISH là sự kiên nhẫn của giảng viên và trợ giảng. Mình phát âm sai từ 'Schedule' cả chục lần vẫn được sửa nhẹ nhàng từng chút một. Khóa học thực sự cứu cánh cho những ai tự ti ngoại ngữ lâu năm."
                        </p>
                    </div>
                    <div class="flex items-center gap-3.5 mt-6 pt-4 border-t border-slate-200">
                        <div class="w-11 h-11 rounded-full bg-emerald-600 text-white font-heading font-bold flex items-center justify-center">
                            L
                        </div>
                        <div>
                            <h4 class="font-heading font-bold text-slate-900 text-sm">Chị Lê Thanh Lan</h4>
                            <p class="text-xs text-slate-500">Nhân viên Kế toán • Học viên Gói Tiêu Chuẩn</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Phần FAQ Accordion -->
            <div id="faq" class="max-w-3xl mx-auto pt-8 border-t border-slate-200">
                <div class="text-center mb-10">
                    <span class="text-accent-600 font-bold text-xs uppercase tracking-wider">Giải đáp thắc mắc cùng TANDAT ENGLISH</span>
                    <h3 class="font-heading font-extrabold text-2xl sm:text-3xl text-slate-900 mt-2">
                        Câu Hỏi Thường Gặp Của Người Mới Bắt Đầu
                    </h3>
                </div>

                <div class="space-y-4">
                    <!-- FAQ Item 1 -->
                    <div class="border border-slate-200 rounded-2xl overflow-hidden bg-slate-50">
                        <button onclick="toggleFaq(1)" class="w-full px-6 py-5 text-left flex items-center justify-between font-heading font-bold text-slate-900 hover:bg-slate-100 transition">
                            <span>1. Mình mất gốc hoàn toàn (chưa biết gì) thì học tại TANDAT ENGLISH có theo kịp không?</span>
                            <i id="faq-icon-1" class="fa-solid fa-chevron-down text-brand-700 transition-transform duration-300 rotate-180"></i>
                        </button>
                        <div id="faq-ans-1" class="px-6 pb-5 text-sm text-slate-600 leading-relaxed">
                            Hoàn toàn theo kịp! Giáo trình của <strong>TANDAT ENGLISH</strong> được thiết kế chuyên biệt từ con số 0. Trong 4 tuần đầu tiên (Phá băng & Chuẩn hóa âm IPA), bạn được hướng dẫn từ cách đặt khẩu hình miệng và có trợ giảng kèm 1-1 sửa bài hàng ngày trước khi bước vào giai đoạn ghép câu.
                        </div>
                    </div>

                    <!-- FAQ Item 2 -->
                    <div class="border border-slate-200 rounded-2xl overflow-hidden bg-slate-50">
                        <button onclick="toggleFaq(2)" class="w-full px-6 py-5 text-left flex items-center justify-between font-heading font-bold text-slate-900 hover:bg-slate-100 transition">
                            <span>2. Nếu mình bận đột xuất nghỉ học thì có được học bù không?</span>
                            <i id="faq-icon-2" class="fa-solid fa-chevron-down text-brand-700 transition-transform duration-300"></i>
                        </button>
                        <div id="faq-ans-2" class="hidden px-6 pb-5 text-sm text-slate-600 leading-relaxed">
                            Có! Toàn bộ buổi học tại <strong>TANDAT ENGLISH</strong> đều có video ghi hình chất lượng cao để bạn xem lại bất cứ lúc nào. Ngoài ra, bạn được hỗ trợ xếp lịch học bù miễn phí hoặc kèm 1-1 cùng trợ giảng để không bị hổng kiến thức.
                        </div>
                    </div>

                    <!-- FAQ Item 3 -->
                    <div class="border border-slate-200 rounded-2xl overflow-hidden bg-slate-50">
                        <button onclick="toggleFaq(3)" class="w-full px-6 py-5 text-left flex items-center justify-between font-heading font-bold text-slate-900 hover:bg-slate-100 transition">
                            <span>3. Cam kết đầu ra bằng văn bản tại TANDAT ENGLISH cụ thể như thế nào?</span>
                            <i id="faq-icon-3" class="fa-solid fa-chevron-down text-brand-700 transition-transform duration-300"></i>
                        </button>
                        <div id="faq-ans-3" class="hidden px-6 pb-5 text-sm text-slate-600 leading-relaxed">
                            Khi đăng ký học, bạn được cam kết lộ trình rõ ràng. Chỉ cần bạn tham gia tối thiểu 85% số buổi học và hoàn thành bài tập thực hành, nếu kết thúc 90 ngày chưa tự tin giao tiếp đầu ra, <strong>TANDAT ENGLISH</strong> hỗ trợ đào tạo lại hoàn toàn miễn phí 100%.
                        </div>
                    </div>

                    <!-- FAQ Item 4 -->
                    <div class="border border-slate-200 rounded-2xl overflow-hidden bg-slate-50">
                        <button onclick="toggleFaq(4)" class="w-full px-6 py-5 text-left flex items-center justify-between font-heading font-bold text-slate-900 hover:bg-slate-100 transition">
                            <span>4. Học phí có được chia nhỏ hoặc trả góp không?</span>
                            <i id="faq-icon-4" class="fa-solid fa-chevron-down text-brand-700 transition-transform duration-300"></i>
                        </button>
                        <div id="faq-ans-4" class="hidden px-6 pb-5 text-sm text-slate-600 leading-relaxed">
                            <strong>TANDAT ENGLISH</strong> hỗ trợ chia học phí thành 2 đợt đóng linh hoạt hoặc trả góp 0% lãi suất cho sinh viên và người đi làm mà vẫn giữ nguyên mức học bổng giảm 40%.
                        </div>
                    </div>
                </div>
            </div>

        </div>
    </section>

    <!-- 8. REGISTRATION FORM WITH VALIDATION & COUNTDOWN TIMER -->
    <section id="dang-ky" class="py-16 sm:py-24 bg-gradient-to-br from-brand-900 via-brand-800 to-slate-900 text-white relative">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
                
                <!-- Cột trái: Thông tin ưu đãi & Đồng hồ đếm ngược -->
                <div class="lg:col-span-6 space-y-6">
                    <span class="inline-flex items-center gap-2 bg-accent-500 text-white text-xs font-bold uppercase tracking-wider px-4 py-1.5 rounded-full">
                        <i class="fa-solid fa-gift"></i> Ưu đãi học bổng TANDAT ENGLISH
                    </span>

                    <h2 class="font-heading font-extrabold text-3xl sm:text-4xl leading-tight">
                        Đăng Ký Học Thử Miễn Phí & Giữ Suất Học Bổng <span class="text-amber-300">40% Học Phí</span>
                    </h2>

                    <p class="text-slate-200 text-base leading-relaxed">
                        Để lại thông tin bên cạnh, Cố vấn học tập của <strong>TANDAT ENGLISH</strong> sẽ liên hệ trong vòng 15 phút để xếp lịch học thử 1-1 và gửi tặng bạn bộ tài liệu tự học phát âm IPA.
                    </p>

                    <!-- Countdown Timer Box -->
                    <div class="bg-white/10 backdrop-blur-md border border-white/20 rounded-3xl p-6">
                        <p class="text-xs font-semibold uppercase tracking-wider text-amber-300 mb-3 flex items-center gap-2">
                            <i class="fa-regular fa-clock"></i> Thời gian còn lại của ưu đãi học bổng:
                        </p>
                        <div class="grid grid-cols-4 gap-3 text-center">
                            <div class="bg-brand-950/70 rounded-2xl p-3 border border-white/10">
                                <span id="cd-days" class="font-heading font-extrabold text-2xl sm:text-3xl text-white block">02</span>
                                <span class="text-[11px] text-slate-300 uppercase">Ngày</span>
                            </div>
                            <div class="bg-brand-950/70 rounded-2xl p-3 border border-white/10">
                                <span id="cd-hours" class="font-heading font-extrabold text-2xl sm:text-3xl text-white block">14</span>
                                <span class="text-[11px] text-slate-300 uppercase">Giờ</span>
                            </div>
                            <div class="bg-brand-950/70 rounded-2xl p-3 border border-white/10">
                                <span id="cd-minutes" class="font-heading font-extrabold text-2xl sm:text-3xl text-white block">38</span>
                                <span class="text-[11px] text-slate-300 uppercase">Phút</span>
                            </div>
                            <div class="bg-brand-950/70 rounded-2xl p-3 border border-white/10">
                                <span id="cd-seconds" class="font-heading font-extrabold text-2xl sm:text-3xl text-amber-300 block">45</span>
                                <span class="text-[11px] text-slate-300 uppercase">Giây</span>
                            </div>
                        </div>
                    </div>

                    <!-- Quà tặng kèm -->
                    <div class="space-y-3 pt-2 text-sm text-slate-200">
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-circle-check text-emerald-400 text-base"></i>
                            <span>Miễn phí 01 buổi <strong>Kiểm tra trình độ & Học thử 1-1</strong> tại TANDAT ENGLISH</span>
                        </div>
                        <div class="flex items-center gap-3">
                            <i class="fa-solid fa-circle-check text-emerald-400 text-base"></i>
                            <span>Tặng ngay Ebook <strong>"1.000 Cụm Từ Giao Tiếp Thực Chiến"</strong> (PDF + Audio)</span>
                        </div>
                    </div>
                </div>

                <!-- Cột phải: Form đăng ký có kiểm tra dữ liệu (Validation) -->
                <div class="lg:col-span-6">
                    <div id="form-card" class="bg-white text-slate-800 rounded-3xl p-7 sm:p-10 shadow-2xl border border-slate-100 transition-all duration-300">
                        <div class="mb-6">
                            <h3 class="font-heading font-extrabold text-2xl text-slate-900">Đăng Ký Tư Vấn Cùng TANDAT ENGLISH</h3>
                            <p class="text-sm text-slate-500 mt-1">Điền thông tin chính xác để nhận lộ trình cá nhân hóa và giữ suất học bổng 40%.</p>
                        </div>

                        <form id="registration-form" onsubmit="handleFormSubmit(event)" novalidate class="space-y-5">
                            <!-- Họ và tên -->
                            <div>
                                <label for="fullname" class="block text-xs font-bold uppercase tracking-wider text-slate-700 mb-2">
                                    Họ và tên của bạn <span class="text-rose-500">*</span>
                                </label>
                                <div class="relative">
                                    <span class="absolute inset-y-0 left-0 pl-4 flex items-center text-slate-400">
                                        <i class="fa-regular fa-user"></i>
                                    </span>
                                    <input type="text" id="fullname" placeholder="VD: Nguyễn Tấn Đạt" class="w-full pl-11 pr-4 py-3.5 rounded-xl border border-slate-300 focus:border-brand-600 focus:ring-2 focus:ring-brand-200 outline-none text-sm transition">
                                </div>
                                <p id="err-fullname" class="hidden text-xs text-rose-600 font-medium mt-1.5">
                                    <i class="fa-solid fa-circle-exclamation mr-1"></i> Vui lòng nhập họ và tên của bạn (tối thiểu 2 ký tự).
                                </p>
                            </div>

                            <!-- Số điện thoại -->
                            <div>
                                <label for="phone" class="block text-xs font-bold uppercase tracking-wider text-slate-700 mb-2">
                                    Số điện thoại (Zalo) <span class="text-rose-500">*</span>
                                </label>
                                <div class="relative">
                                    <span class="absolute inset-y-0 left-0 pl-4 flex items-center text-slate-400">
                                        <i class="fa-solid fa-phone"></i>
                                    </span>
                                    <input type="tel" id="phone" placeholder="VD: 0912345678" class="w-full pl-11 pr-4 py-3.5 rounded-xl border border-slate-300 focus:border-brand-600 focus:ring-2 focus:ring-brand-200 outline-none text-sm transition">
                                </div>
                                <p id="err-phone" class="hidden text-xs text-rose-600 font-medium mt-1.5">
                                    <i class="fa-solid fa-circle-exclamation mr-1"></i> Vui lòng nhập số điện thoại hợp lệ (10 chữ số, bắt đầu bằng số 0).
                                </p>
                            </div>

                            <!-- Đối tượng & Mục tiêu học -->
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                                <div>
                                    <label for="goal" class="block text-xs font-bold uppercase tracking-wider text-slate-700 mb-2">
                                        Mục tiêu học hiện tại
                                    </label>
                                    <select id="goal" class="w-full px-4 py-3.5 rounded-xl border border-slate-300 focus:border-brand-600 focus:ring-2 focus:ring-brand-200 outline-none text-sm bg-white">
                                        <option value="Sinh viên cần giao tiếp & ra trường">Sinh viên (Giao tiếp & Ra trường)</option>
                                        <option value="Người đi làm cần giao tiếp công việc">Người đi làm (Giao tiếp & Phỏng vấn)</option>
                                        <option value="Người mất gốc lâu năm muốn học lại">Mất gốc lâu năm muốn học từ đầu</option>
                                        <option value="Tiếng Anh du lịch & định cư">Tiếng Anh du lịch & Đời sống</option>
                                    </select>
                                </div>

                                <!-- Gói khóa học quan tâm -->
                                <div>
                                    <label for="package" class="block text-xs font-bold uppercase tracking-wider text-slate-700 mb-2">
                                        Gói khóa học quan tâm
                                    </label>
                                    <select id="package" class="w-full px-4 py-3.5 rounded-xl border border-slate-300 focus:border-brand-600 focus:ring-2 focus:ring-brand-200 outline-none text-sm bg-white font-medium text-brand-900">
                                        <option value="Gói Tiêu Chuẩn - Bán chạy nhất (3.490.000đ)">Gói Tiêu Chuẩn (3.490.000đ)</option>
                                        <option value="Gói Cơ Bản (1.890.000đ)">Gói Cơ Bản (1.890.000đ)</option>
                                        <option value="Gói VIP Kèm 1-1 (5.690.000đ)">Gói VIP Kèm 1-1 (5.690.000đ)</option>
                                        <option value="Cần tư vấn chọn gói phù hợp">Cần tư vấn thêm</option>
                                    </select>
                                </div>
                            </div>

                            <!-- Nút Gửi Đăng Ký -->
                            <button type="submit" class="w-full bg-accent-500 hover:bg-accent-600 text-white font-heading font-bold text-base py-4 rounded-2xl shadow-glow hover:-translate-y-0.5 transition-all flex items-center justify-center gap-2">
                                <span>Hoàn Tất Đăng Ký Tại TANDAT ENGLISH</span>
                                <i class="fa-solid fa-paper-plane"></i>
                            </button>

                            <p class="text-[11px] text-slate-400 text-center">
                                <i class="fa-solid fa-lock mr-1"></i> Thông tin của bạn được bảo mật tuyệt đối 100% tại TANDAT ENGLISH.
                            </p>
                        </form>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- FOOTER (TANDAT ENGLISH) -->
    <footer class="bg-slate-950 text-slate-400 py-12 border-t border-slate-800 text-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col sm:flex-row items-center justify-between gap-6">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-brand-700 to-accent-500 flex items-center justify-center text-white">
                    <i class="fa-solid fa-graduation-cap"></i>
                </div>
                <div>
                    <span class="font-heading font-extrabold text-white block">TANDAT ENGLISH</span>
                    <span class="text-xs text-slate-500">Hệ thống đào tạo Tiếng Anh Cho Người Mới Bắt Đầu • Kèm 1-1 chuẩn IPA</span>
                </div>
            </div>
            <div class="flex flex-wrap items-center gap-4">
                <span class="text-xs text-slate-500">© 2026 TANDAT ENGLISH. All rights reserved.</span>
            </div>
        </div>
    </footer>

    <!-- MODAL XÁC NHẬN ĐĂNG KÝ THÀNH CÔNG -->
    <div id="success-modal" class="fixed inset-0 z-50 hidden bg-slate-900/70 backdrop-blur-sm flex items-center justify-center p-4">
        <div class="bg-white rounded-3xl max-w-md w-full p-7 sm:p-8 text-center shadow-2xl border border-slate-100 animate-fade-in">
            <div class="w-16 h-16 rounded-full bg-emerald-100 text-emerald-600 flex items-center justify-center text-3xl mx-auto mb-4">
                <i class="fa-solid fa-circle-check"></i>
            </div>
            <h3 class="font-heading font-extrabold text-2xl text-slate-900">Đăng Ký Thành Công!</h3>
            <p class="text-sm text-slate-600 mt-2">
                Chúc mừng <strong id="modal-student-name" class="text-brand-800">bạn</strong> đã giữ suất học bổng 40% tại <strong>TANDAT ENGLISH</strong>.
            </p>
            <div class="bg-slate-50 rounded-2xl p-4 my-5 text-left text-xs space-y-2 border border-slate-200">
                <div class="flex justify-between">
                    <span class="text-slate-500">Số điện thoại:</span>
                    <strong id="modal-student-phone" class="text-slate-800"></strong>
                </div>
                <div class="flex justify-between">
                    <span class="text-slate-500">Gói đã chọn:</span>
                    <strong id="modal-student-package" class="text-brand-700"></strong>
                </div>
                <div class="flex justify-between">
                    <span class="text-slate-500">Mục tiêu:</span>
                    <strong id="modal-student-goal" class="text-slate-800"></strong>
                </div>
            </div>
            <p class="text-xs text-slate-500 mb-6">
                Cố vấn học tập của <strong>TANDAT ENGLISH</strong> sẽ liên hệ qua Zalo trong ít phút tới để gửi lịch học thử 1-1 và bộ quà tặng Ebook IPA.
            </p>
            <button onclick="closeSuccessModal()" class="w-full bg-brand-800 hover:bg-brand-900 text-white font-heading font-bold py-3.5 rounded-xl transition">
                Đã hiểu, quay lại trang chủ
            </button>
        </div>
    </div>

    <!-- JAVASCRIPT XỬ LÝ TOÀN BỘ TƯƠNG TÁC -->
    <script>
        // ==========================================
        // 1. DỮ LIỆU LỘ TRÌNH 3 GIAI ĐOẠN TANDAT ENGLISH
        // ==========================================
        const stagesData = {
            1: {
                badge: "Giai đoạn 1 • Tuần 1 đến Tuần 4",
                title: "Phá Băng & Chuẩn Hóa Âm IPA (44 Âm Quốc Tế)",
                desc: "Chấm dứt hoàn toàn thói quen đọc tiếng Anh theo kiểu 'Việt hóa'. Tại TANDAT ENGLISH, bạn sẽ làm chủ khẩu hình miệng, trọng âm từ và nghe bắt âm chuẩn xác.",
                outcomes: [
                    "Nhìn phiên âm quốc tế IPA tự đọc đúng 100% bất kỳ từ mới nào trong từ điển.",
                    "Phát âm rõ âm đuôi (Ending sounds), phân biệt nguyên âm ngắn - dài chuẩn xác.",
                    "Hiểu quy tắc nối âm (Linking sounds) giúp nghe người bản xứ dễ dàng hơn."
                ],
                weeks: [
                    { week: "Tuần 1", topic: "20 Nguyên âm đơn & Nguyên âm đôi", detail: "Khẩu hình miệng âm /ɪ/ - /i:/, /æ/ - /e/, /ʊ/ - /u:/" },
                    { week: "Tuần 2", topic: "24 Phụ âm & Các cặp âm dễ nhầm lẫn", detail: "Chinh phục âm /θ/, /ð/, /ʃ/, /ʒ/, /tʃ/, /dʒ/" },
                    { week: "Tuần 3", topic: "Trọng âm từ (Word Stress) & Âm câm", detail: "Quy tắc nhấn trọng âm và 50 từ chứa âm câm phổ biến" },
                    { week: "Tuần 4", topic: "Ngữ điệu câu & Thực hành Shadowing", detail: "Luyện nhại giọng theo ngữ điệu lên xuống tự nhiên" }
                ]
            },
            2: {
                badge: "Giai đoạn 2 • Tuần 5 đến Tuần 8",
                title: "Xây Nền Từ Vựng & Phản Xạ Câu Thực Chiến",
                desc: "Áp dụng phương pháp học theo cụm từ (Chunking) và lặp lại ngắt quãng của TANDAT ENGLISH giúp bạn bật ra câu hoàn chỉnh trong 3 giây mà không cần dịch ngầm.",
                outcomes: [
                    "Sở hữu 1.000 từ vựng và 150 cụm từ chiếm 85% hội thoại giao tiếp hàng ngày.",
                    "Nắm vững 12 cấu trúc câu cốt lõi để diễn đạt ý muốn ở quá khứ, hiện tại, tương lai.",
                    "Tăng tốc độ phản xạ nghe - hiểu câu hỏi và trả lời ngay lập tức."
                ],
                weeks: [
                    { week: "Tuần 5", topic: "Chủ đề Bản thân, Gia đình & Thói quen", detail: "250 cụm từ mô tả lịch trình và sở thích cá nhân" },
                    { week: "Tuần 6", topic: "Chủ đề Mua sắm, Ẩm thực & Di chuyển", detail: "Cách đặt món, hỏi đường, mặc cả và thanh toán" },
                    { week: "Tuần 7", topic: "Chủ đề Công sở, Email & Điện thoại", detail: "Mẫu câu hẹn lịch, trao đổi công việc cơ bản" },
                    { week: "Tuần 8", topic: "Kể chuyện & Bày tỏ quan điểm cá nhân", detail: "Kết nối câu dài mượt mà bằng các từ nối tự nhiên" }
                ]
            },
            3: {
                badge: "Giai đoạn 3 • Tuần 9 đến Tuần 12",
                title: "Giao Tiếp Thực Chiến & Thuyết Trình Tự Tin",
                desc: "Đóng vai thực hành trực tiếp 1-1 cùng giảng viên TANDAT ENGLISH trong các tình huống đời sống, du lịch và phỏng vấn xin việc thực tế.",
                outcomes: [
                    "Tự tin bắt chuyện và duy trì cuộc hội thoại kéo dài 15-20 phút với người nước ngoài.",
                    "Xử lý tình huống bất ngờ khi đi du lịch nước ngoài (sân bay, khách sạn, hải quan).",
                    "Tự tin giới thiệu bản thân, trả lời phỏng vấn và thuyết trình ngắn bằng tiếng Anh."
                ],
                weeks: [
                    { week: "Tuần 9", topic: "Thực chiến Tiếng Anh Du lịch & Sân bay", detail: "Làm thủ tục check-in, nhập cảnh, đặt phòng khách sạn" },
                    { week: "Tuần 10", topic: "Thực chiến Giao tiếp Công sở & Họp nhóm", detail: "Đưa ý kiến trong cuộc họp, báo cáo tiến độ công việc" },
                    { week: "Tuần 11", topic: "Chinh phục Phỏng vấn Tiếng Anh", detail: "Trả lời 15 câu hỏi phỏng vấn phổ biến nhất của HR" },
                    { week: "Tuần 12", topic: "Thuyết trình Cuối khóa & Cấp Chứng nhận", detail: "Thuyết trình tự tin & Đánh giá đầu ra 1-1 tại TANDAT ENGLISH" }
                ]
            }
        };

        function selectStage(stageNum) {
            // Cập nhật giao diện các nút tab
            for (let i = 1; i <= 3; i++) {
                const btn = document.getElementById(`stage-btn-${i}`);
                if (i === stageNum) {
                    btn.className = "stage-btn text-left p-5 rounded-2xl border-2 transition-all bg-brand-900 text-white border-brand-900 shadow-lg";
                } else {
                    btn.className = "stage-btn text-left p-5 rounded-2xl border-2 transition-all bg-white text-slate-800 border-slate-200 hover:border-brand-400";
                }
            }

            // Render nội dung chi tiết
            const data = stagesData[stageNum];
            const panel = document.getElementById('stage-content-panel');

            const outcomesHtml = data.outcomes.map(item => `
                <li class="flex items-start gap-3">
                    <span class="w-5 h-5 rounded-full bg-emerald-100 text-emerald-600 flex items-center justify-center text-xs shrink-0 mt-0.5">
                        <i class="fa-solid fa-check"></i>
                    </span>
                    <span class="text-slate-700 text-sm">${item}</span>
                </li>
            `).join('');

            const weeksHtml = data.weeks.map(w => `
                <div class="bg-slate-50 rounded-2xl p-4 border border-slate-200/80">
                    <span class="text-xs font-bold text-accent-600 uppercase">${w.week}</span>
                    <h5 class="font-heading font-bold text-slate-900 text-sm mt-1">${w.topic}</h5>
                    <p class="text-xs text-slate-500 mt-1">${w.detail}</p>
                </div>
            `).join('');

            panel.innerHTML = `
                <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center">
                    <div class="lg:col-span-6 space-y-4">
                        <span class="inline-block text-xs font-bold uppercase tracking-wider bg-brand-50 text-brand-700 px-3 py-1 rounded-full">
                            ${data.badge}
                        </span>
                        <h3 class="font-heading font-extrabold text-2xl sm:text-3xl text-slate-900">
                            ${data.title}
                        </h3>
                        <p class="text-slate-600 text-sm sm:text-base leading-relaxed">
                            ${data.desc}
                        </p>
                        <div class="pt-2">
                            <h4 class="font-heading font-bold text-sm uppercase tracking-wider text-slate-900 mb-3">
                                Kết quả đạt được sau giai đoạn này:
                            </h4>
                            <ul class="space-y-2.5">
                                ${outcomesHtml}
                            </ul>
                        </div>
                    </div>
                    <div class="lg:col-span-6">
                        <div class="bg-brand-50/60 rounded-2xl p-5 border border-brand-100">
                            <h4 class="font-heading font-bold text-sm text-brand-900 mb-4 flex items-center gap-2">
                                <i class="fa-regular fa-calendar-check text-brand-700"></i>
                                Lịch trình học chi tiết từng tuần
                            </h4>
                            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3.5">
                                ${weeksHtml}
                            </div>
                        </div>
                    </div>
                </div>
            `;
        }

        // ==========================================
        // 2. WEB SPEECH API & FLASHCARD FLIP
        // ==========================================
        function flipCard(cardId) {
            const card = document.getElementById(cardId);
            if (card) {
                card.classList.toggle('flipped');
            }
        }

        function speakSampleText(text) {
            const statusBadge = document.getElementById('speech-status');
            if ('speechSynthesis' in window) {
                window.speechSynthesis.cancel();
                const utterance = new SpeechSynthesisUtterance(text);
                utterance.lang = 'en-US';
                utterance.rate = 0.9; // Tốc độ vừa phải cho người mới bắt đầu nghe rõ
                
                if (statusBadge) {
                    statusBadge.innerHTML = `<i class="fa-solid fa-volume-high text-accent-500 animate-pulse mr-1"></i> Đang phát: "${text.split('.')[0]}"...`;
                }

                utterance.onend = () => {
                    if (statusBadge) {
                        statusBadge.innerHTML = `<i class="fa-solid fa-circle-check text-emerald-500 mr-1"></i> Đã phát âm xong`;
                    }
                };
                window.speechSynthesis.speak(utterance);
            } else {
                if (statusBadge) {
                    statusBadge.innerHTML = `<i class="fa-solid fa-circle-info text-amber-500 mr-1"></i> Trình duyệt chưa hỗ trợ phát giọng nói`;
                }
            }
        }

        // ==========================================
        // 3. CHUYỂN ĐỔI TAB HỌC THỬ & BÀI TEST 3 CÂU
        // ==========================================
        function switchDemoTab(tab) {
            const flashcardTab = document.getElementById('demo-tab-flashcard');
            const quizTab = document.getElementById('demo-tab-quiz');
            const btnFlashcard = document.getElementById('tab-btn-flashcard');
            const btnQuiz = document.getElementById('tab-btn-quiz');

            if (tab === 'flashcard') {
                flashcardTab.classList.remove('hidden');
                quizTab.classList.add('hidden');
                btnFlashcard.className = "px-5 py-3 rounded-xl font-heading font-bold text-sm transition-all bg-brand-800 text-white shadow";
                btnQuiz.className = "px-5 py-3 rounded-xl font-heading font-bold text-sm transition-all text-slate-600 hover:text-slate-900";
            } else {
                flashcardTab.classList.add('hidden');
                quizTab.classList.remove('hidden');
                btnQuiz.className = "px-5 py-3 rounded-xl font-heading font-bold text-sm transition-all bg-brand-800 text-white shadow";
                btnFlashcard.className = "px-5 py-3 rounded-xl font-heading font-bold text-sm transition-all text-slate-600 hover:text-slate-900";
                renderQuiz();
            }
        }

        const quizQuestions = [
            {
                q: "Câu 1/3 (Phát âm): Từ 'Comfortable' (Thoải mái) có bao nhiêu âm tiết khi người bản xứ phát âm chuẩn?",
                options: [
                    "A. 4 âm tiết (Com - for - ta - ble)",
                    "B. 3 âm tiết (KUM - fơ - bồ)",
                    "C. 2 âm tiết (Com - bồ)"
                ],
                correct: 1,
                explanation: "Chính xác! Người bản xứ lược âm ở giữa và chỉ đọc 3 âm tiết là /ˈkʌm.fə.tə.bəl/."
            },
            {
                q: "Câu 2/3 (Phản xạ giao tiếp): Khi đồng nghiệp nước ngoài hỏi 'How’s it going?', câu trả lời tự nhiên nhất là gì?",
                options: [
                    "A. I am going to the office now.",
                    "B. Pretty good, thanks! How about you?",
                    "C. Yes, it is going."
                ],
                correct: 1,
                explanation: "'How’s it going?' có nghĩa là 'Dạo này bạn thế nào?' (tương tự How are you?), không phải hỏi bạn đang đi đâu."
            },
            {
                q: "Câu 3/3 (Từ vựng thực tế): Để nói 'Hôm nay tôi rất bận nhiều việc' một cách tự nhiên như người bản xứ, bạn dùng cụm nào?",
                options: [
                    "A. I have a lot on my plate today.",
                    "B. Today my job is very big.",
                    "C. I am busy many things today."
                ],
                correct: 0,
                explanation: "Cụm 'have a lot on one’s plate' là cụm từ cực kỳ thông dụng trong giao tiếp để diễn tả đang có nhiều việc phải giải quyết."
            }
        ];

        let currentQuizIndex = 0;
        let quizScore = 0;

        function renderQuiz() {
            const container = document.getElementById('quiz-container');
            if (currentQuizIndex >= quizQuestions.length) {
                // Hiển thị kết quả
                let recommendedPkg = "Gói Tiêu Chuẩn (Pro Giao Tiếp - 3.490.000đ)";
                let levelComment = "Bạn đã có sự nhạy bén ban đầu nhưng cần hệ thống hóa lại 44 âm IPA và các cụm phản xạ thực tế để giao tiếp trôi chảy.";
                if (quizScore === 3) {
                    levelComment = "Tuyệt vời! Nền tảng của bạn khá tốt. Bạn rất phù hợp với Gói Pro Giao Tiếp hoặc Gói Kèm 1-1 VIP để bứt tốc phản xạ.";
                } else if (quizScore <= 1) {
                    levelComment = "Đừng lo lắng! 90% học viên mới bắt đầu đều nhầm các câu này. Lộ trình 90 ngày từ gốc sẽ giúp bạn nắm chắc từng bước.";
                }

                container.innerHTML = `
                    <div class="text-center space-y-4">
                        <div class="w-16 h-16 rounded-2xl bg-emerald-100 text-emerald-600 flex items-center justify-center text-3xl mx-auto">
                            <i class="fa-solid fa-award"></i>
                        </div>
                        <span class="text-xs font-bold uppercase text-brand-700 bg-brand-50 px-3 py-1 rounded-full">Kết quả bài test nhanh</span>
                        <h3 class="font-heading font-extrabold text-2xl text-slate-900">
                            Bạn trả lời đúng <span class="text-accent-600">${quizScore}/${quizQuestions.length}</span> câu!
                        </h3>
                        <p class="text-sm text-slate-600 max-w-lg mx-auto">${levelComment}</p>
                        <div class="pt-4 flex flex-col sm:flex-row items-center justify-center gap-3">
                            <button onclick="selectPackageAndScroll('${recommendedPkg}')" class="w-full sm:w-auto bg-accent-500 hover:bg-accent-600 text-white font-heading font-bold text-sm px-6 py-3.5 rounded-xl shadow-glow transition">
                                Nhận lộ trình phù hợp & Giảm 40% →
                            </button>
                            <button onclick="resetQuiz()" class="w-full sm:w-auto bg-white hover:bg-slate-100 text-slate-700 border border-slate-300 font-heading font-bold text-sm px-5 py-3.5 rounded-xl transition">
                                Làm lại bài test
                            </button>
                        </div>
                    </div>
                `;
                return;
            }

            const item = quizQuestions[currentQuizIndex];
            const optionsHtml = item.options.map((opt, idx) => `
                <button onclick="answerQuiz(${idx})" class="w-full text-left p-4 rounded-2xl border border-slate-200 bg-white hover:border-brand-600 hover:bg-brand-50/50 font-medium text-sm text-slate-800 transition flex items-center justify-between group">
                    <span>${opt}</span>
                    <i class="fa-solid fa-chevron-right text-slate-300 group-hover:text-brand-600"></i>
                </button>
            `).join('');

            container.innerHTML = `
                <div class="space-y-5">
                    <div class="flex items-center justify-between text-xs font-bold text-slate-400 uppercase">
                        <span>Kiểm tra nhanh trình độ</span>
                        <span>Tiến độ: ${currentQuizIndex + 1} / ${quizQuestions.length}</span>
                    </div>
                    <h4 class="font-heading font-bold text-lg sm:text-xl text-slate-900">${item.q}</h4>
                    <div class="space-y-3">
                        ${optionsHtml}
                    </div>
                </div>
            `;
        }

        function answerQuiz(selectedIndex) {
            const item = quizQuestions[currentQuizIndex];
            if (selectedIndex === item.correct) {
                quizScore++;
            }
            currentQuizIndex++;
            renderQuiz();
        }

        function resetQuiz() {
            currentQuizIndex = 0;
            quizScore = 0;
            renderQuiz();
        }

        // ==========================================
        // 4. CHỌN GÓI HỌC & CUỘN XUỐNG FORM ĐĂNG KÝ
        // ==========================================
        function selectPackageAndScroll(pkgName) {
            const selectEl = document.getElementById('package');
            if (selectEl) {
                selectEl.value = pkgName;
            }
            const formSection = document.getElementById('dang-ky');
            if (formSection) {
                formSection.scrollIntoView({ behavior: 'smooth' });
            }
            // Hiệu ứng nháy sáng nhẹ ở khung Form
            const formCard = document.getElementById('form-card');
            if (formCard) {
                formCard.classList.add('ring-4', 'ring-accent-500');
                setTimeout(() => {
                    formCard.classList.remove('ring-4', 'ring-accent-500');
                }, 1800);
            }
        }

        // ==========================================
        // 5. FAQ ACCORDION
        // ==========================================
        function toggleFaq(index) {
            const ans = document.getElementById(`faq-ans-${index}`);
            const icon = document.getElementById(`faq-icon-${index}`);
            if (ans && icon) {
                ans.classList.toggle('hidden');
                icon.classList.toggle('rotate-180');
            }
        }

        // ==========================================
        // 6. MOBILE MENU TOGGLE
        // ==========================================
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu');
            const icon = document.getElementById('mobile-menu-icon');
            if (menu) {
                menu.classList.toggle('hidden');
                if (menu.classList.contains('hidden')) {
                    icon.className = "fa-solid fa-bars text-xl";
                } else {
                    icon.className = "fa-solid fa-xmark text-xl";
                }
            }
        }

        // ==========================================
        // 7. KIỂM TRA DỮ LIỆU FORM (VALIDATION) & MODAL
        // ==========================================
        function handleFormSubmit(e) {
            e.preventDefault();
            const fullnameInput = document.getElementById('fullname');
            const phoneInput = document.getElementById('phone');
            const goalSelect = document.getElementById('goal');
            const packageSelect = document.getElementById('package');

            const errName = document.getElementById('err-fullname');
            const errPhone = document.getElementById('err-phone');

            const nameVal = fullnameInput.value.trim();
            const phoneVal = phoneInput.value.trim();

            let isValid = true;

            // Validate Họ tên
            if (nameVal.length < 2) {
                errName.classList.remove('hidden');
                fullnameInput.classList.add('border-rose-500');
                isValid = false;
            } else {
                errName.classList.add('hidden');
                fullnameInput.classList.remove('border-rose-500');
            }

            // Validate Số điện thoại Việt Nam (10 số, bắt đầu bằng 0)
            const phoneRegex = /^0\d{9}$/;
            if (!phoneRegex.test(phoneVal)) {
                errPhone.classList.remove('hidden');
                phoneInput.classList.add('border-rose-500');
                isValid = false;
            } else {
                errPhone.classList.add('hidden');
                phoneInput.classList.remove('border-rose-500');
            }

            if (!isValid) return;

            // ====== GỬI THÔNG TIN VỀ GMAIL (qua FormSubmit) ======
            const NHAN_MAIL_TAI = "bussulol1407@gmail.com";

            const submitBtn = e.target.querySelector('button[type="submit"]');
            const btnHTML = submitBtn.innerHTML;
            submitBtn.disabled = true;
            submitBtn.innerHTML = '<span>Đang gửi...</span>';

            fetch("https://formsubmit.co/ajax/" + NHAN_MAIL_TAI, {
                method: "POST",
                headers: { "Content-Type": "application/json", "Accept": "application/json" },
                body: JSON.stringify({
                    _subject: "Đăng ký mới TANDAT ENGLISH: " + nameVal + " - " + phoneVal,
                    _template: "table",
                    _captcha: "false",
                    "Họ và tên": nameVal,
                    "Số điện thoại": phoneVal,
                    "Mục tiêu học": goalSelect.value,
                    "Gói quan tâm": packageSelect.value
                })
            })
            .then(r => r.json())
            .then(data => {
                if (String(data.success) !== "true") throw new Error(data.message || "Gửi thất bại");
                document.getElementById('modal-student-name').textContent = nameVal;
                document.getElementById('modal-student-phone').textContent = phoneVal;
                document.getElementById('modal-student-package').textContent = packageSelect.value;
                document.getElementById('modal-student-goal').textContent = goalSelect.value;
                document.getElementById('success-modal').classList.remove('hidden');
                document.getElementById('registration-form').reset();
            })
            .catch(() => {
                alert("Gửi đăng ký chưa thành công. Vui lòng thử lại hoặc liên hệ trực tiếp trung tâm.");
            })
            .finally(() => {
                submitBtn.disabled = false;
                submitBtn.innerHTML = btnHTML;
            });
        }

        function closeSuccessModal() {
            document.getElementById('success-modal').classList.add('hidden');
        }

        // ==========================================
        // 9. ĐỒNG HỒ ĐẾM NGƯỢC ƯU ĐÃI (COUNTDOWN TIMER)
        // ==========================================
        function startCountdown() {
            let totalSeconds = (2 * 86400) + (14 * 3600) + (38 * 60) + 45;
            setInterval(() => {
                if (totalSeconds <= 0) totalSeconds = 86400;
                totalSeconds--;

                const d = Math.floor(totalSeconds / 86400);
                const h = Math.floor((totalSeconds % 86400) / 3600);
                const m = Math.floor((totalSeconds % 3600) / 60);
                const s = totalSeconds % 60;

                document.getElementById('cd-days').textContent = String(d).padStart(2, '0');
                document.getElementById('cd-hours').textContent = String(h).padStart(2, '0');
                document.getElementById('cd-minutes').textContent = String(m).padStart(2, '0');
                document.getElementById('cd-seconds').textContent = String(s).padStart(2, '0');
            }, 1000);
        }

        // Khởi tạo dữ liệu khi tải trang
        window.onload = function () {
            selectStage(1);
            renderQuiz();
            startCountdown();
        };
    </script>
</body>
</html>
