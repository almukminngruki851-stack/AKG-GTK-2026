
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplikasi Latihan AKG GTK Kemenag - 100 Soal</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        body { font-family: 'Inter', sans-serif; }
        .custom-scrollbar::-webkit-scrollbar { width: 6px; }
        .custom-scrollbar::-webkit-scrollbar-track { background: #f1f5f9; border-radius: 4px; }
        .custom-scrollbar::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 4px; }
        .custom-scrollbar::-webkit-scrollbar-thumb:hover { background: #94a3b8; }
    </style>
</head>
<body class="bg-slate-100 min-h-screen text-slate-800 flex flex-col">

    <!-- HEADER / NAVBAR -->
    <header class="bg-emerald-700 text-white shadow-md py-3.5 px-4 md:px-8 sticky top-0 z-50">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <div class="flex items-center space-x-3">
                <div class="bg-white/20 p-2 rounded-xl">
                    <i data-lucide="book-open" class="w-6 h-6 text-yellow-300"></i>
                </div>
                <div>
                    <h1 class="font-bold text-base md:text-lg leading-tight">CBT AKG GTK Kemenag</h1>
                    <p class="text-xs text-emerald-200">Asesmen Kompetensi Guru (100 Soal per Mapel)</p>
                </div>
            </div>
            
            <div id="headerQuizInfo" class="hidden flex items-center space-x-4">
                <div class="bg-emerald-800/80 backdrop-blur px-3.5 py-1.5 rounded-lg border border-emerald-600 flex items-center space-x-2">
                    <i data-lucide="clock" class="w-4 h-4 text-amber-300"></i>
                    <span id="timerDisplay" class="font-mono text-sm font-bold text-yellow-300">02:00:00</span>
                </div>
                <div class="hidden md:block text-right text-xs bg-emerald-800 px-3 py-1.5 rounded-lg border border-emerald-600">
                    <span id="badgeNama" class="font-semibold text-yellow-300"></span> 
                    (<span id="badgeMapel"></span> - <span id="badgeJenjang"></span>)
                </div>
            </div>
        </div>
    </header>

    <!-- MAIN CONTENT -->
    <main class="max-w-7xl mx-auto p-4 md:p-6 flex-1 w-full">

        <!-- SCREEN 1: FORM REGISTRASI -->
        <section id="screenRegister" class="bg-white rounded-2xl shadow-xl p-6 md:p-10 max-w-xl mx-auto mt-4 border border-slate-200">
            <div class="text-center mb-6">
                <div class="w-16 h-16 bg-emerald-100 text-emerald-700 rounded-2xl flex items-center justify-center mx-auto mb-3 shadow-inner">
                    <i data-lucide="user-check" class="w-8 h-8"></i>
                </div>
                <h2 class="text-2xl font-bold text-slate-800">Registrasi Peserta AKG</h2>
                <p class="text-slate-500 text-sm mt-1">Sistem Ujian Simulasi AKG GTK (100 Soal / 120 Menit)</p>
            </div>

            <form id="formStart" onsubmit="handleStartQuiz(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold uppercase text-slate-600 mb-1">Nama Lengkap & Gelar</label>
                    <input type="text" id="inputNama" required placeholder="Contoh: Ustadz Ahmad Fauzi, M.Pd." 
                           class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:ring-2 focus:ring-emerald-500 focus:border-emerald-500 outline-none transition text-sm">
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-semibold uppercase text-slate-600 mb-1">Satuan Pendidikan</label>
                        <select id="selectJenjang" required class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:ring-2 focus:ring-emerald-500 focus:border-emerald-500 outline-none transition text-sm">
                            <option value="">-- Pilih Jenjang --</option>
                            <option value="MTs">MTs (Tsanawiyah)</option>
                            <option value="MA">MA (Aliyah)</option>
                        </select>
                    </div>

                    <div>
                        <label class="block text-xs font-semibold uppercase text-slate-600 mb-1">Mata Pelajaran</label>
                        <select id="selectMapel" required class="w-full px-4 py-2.5 rounded-xl border border-slate-300 focus:ring-2 focus:ring-emerald-500 focus:border-emerald-500 outline-none transition text-sm">
                            <option value="">-- Pilih Mapel --</option>
                            <option value="Al-Qur'an Hadis">Al-Qur'an Hadis</option>
                            <option value="Bahasa Arab">Bahasa Arab</option>
                            <option value="Bahasa Inggris">Bahasa Inggris</option>
                            <option value="Matematika">Matematika</option>
                            <option value="IPA">IPA</option>
                            <option value="IPS">IPS</option>
                        </select>
                    </div>
                </div>

                <div class="bg-emerald-50 border border-emerald-200 rounded-xl p-4 text-xs text-emerald-800 space-y-1">
                    <p class="font-bold flex items-center gap-1">
                        <i data-lucide="info" class="w-4 h-4"></i> Ketentuan Simulasi:
                    </p>
                    <ul class="list-disc list-inside space-y-0.5 text-emerald-700">
                        <li>Jumlah soal: <strong>100 Butir Soal</strong></li>
                        <li>Alokasi waktu: <strong>120 Menit</strong></li>
                        <li>Terdapat tombol acak nomor & fitur ragu-ragu</li>
                    </ul>
                </div>

                <button type="submit" class="w-full bg-emerald-600 hover:bg-emerald-700 text-white font-semibold py-3 rounded-xl shadow-lg hover:shadow-xl transition flex items-center justify-center space-x-2 text-sm">
                    <span>Mulai Mengerjakan 100 Soal</span>
                    <i data-lucide="arrow-right" class="w-4 h-4"></i>
                </button>
            </form>
        </section>

        <!-- SCREEN 2: LEMBAR UJIAN (CBT ENGINE) -->
        <section id="screenQuiz" class="hidden grid grid-cols-1 lg:grid-cols-4 gap-6">
            
            <!-- Area Lembar Soal (3 Kolom) -->
            <div class="lg:col-span-3 space-y-4">
                <div class="bg-white rounded-2xl shadow-md p-6 border border-slate-200">
                    
                    <!-- Top Bar Info & Progress -->
                    <div class="flex flex-wrap justify-between items-center border-b pb-4 mb-5 gap-2">
                        <div class="flex items-center space-x-2">
                            <span class="text-xs font-bold uppercase bg-emerald-100 text-emerald-800 px-3 py-1 rounded-full border border-emerald-200" id="quizHeaderInfo">
                                Soal No. 1 dari 100
                            </span>
                            <span id="flagBadge" class="hidden text-xs bg-amber-100 text-amber-800 font-semibold px-2.5 py-1 rounded-full border border-amber-300">
                                Ditandai Ragu-Ragu
                            </span>
                        </div>
                        <div class="text-xs font-medium text-slate-500">
                            Progres: <span id="answeredCount" class="font-bold text-emerald-600">0</span> / 100 Terjawab
                        </div>
                    </div>

                    <!-- Progress Bar -->
                    <div class="w-full bg-slate-100 rounded-full h-2 mb-6 overflow-hidden">
                        <div id="progressBar" class="bg-emerald-600 h-2 rounded-full transition-all duration-300" style="width: 0%"></div>
                    </div>

                    <!-- Teks Soal -->
                    <div class="text-slate-800 font-medium text-base md:text-lg leading-relaxed mb-6" id="questionText">
                        <!-- Di-generate JS -->
                    </div>

                    <!-- Pilihan Jawaban -->
                    <div class="space-y-3" id="optionsContainer">
                        <!-- Pilihan A, B, C, D di-generate JS -->
                    </div>
                </div>

                <!-- Navigasi Soal -->
                <div class="bg-white rounded-2xl shadow-md p-4 flex flex-wrap gap-2 justify-between items-center border border-slate-200">
                    <button onclick="navigateQuestion(-1)" id="btnPrev" class="px-4 py-2.5 bg-slate-100 hover:bg-slate-200 text-slate-700 font-medium rounded-xl text-xs md:text-sm flex items-center space-x-1.5 transition">
                        <i data-lucide="chevron-left" class="w-4 h-4"></i>
                        <span>Sebelumnya</span>
                    </button>

                    <div class="flex items-center space-x-2">
                        <button onclick="toggleDoubt()" id="btnDoubt" class="px-4 py-2.5 bg-amber-100 hover:bg-amber-200 text-amber-800 font-medium rounded-xl text-xs md:text-sm flex items-center space-x-1.5 border border-amber-300 transition">
                            <i data-lucide="flag" class="w-4 h-4 text-amber-600"></i>
                            <span>Ragu-Ragu</span>
                        </button>

                        <button onclick="randomQuestion()" class="px-4 py-2.5 bg-slate-800 hover:bg-slate-900 text-white font-medium rounded-xl text-xs md:text-sm flex items-center space-x-1.5 shadow transition">
                            <i data-lucide="shuffle" class="w-4 h-4"></i>
                            <span class="hidden sm:inline">Acak Soal</span>
                        </button>
                    </div>

                    <button onclick="navigateQuestion(1)" id="btnNext" class="px-4 py-2.5 bg-slate-100 hover:bg-slate-200 text-slate-700 font-medium rounded-xl text-xs md:text-sm flex items-center space-x-1.5 transition">
                        <span>Selanjutnya</span>
                        <i data-lucide="chevron-right" class="w-4 h-4"></i>
                    </button>
                </div>
            </div>

            <!-- Palet / Grid 100 Nomor Soal (1 Kolom) -->
            <div class="lg:col-span-1">
                <div class="bg-white rounded-2xl shadow-md p-4 sticky top-20 border border-slate-200 flex flex-col max-h-[82vh]">
                    <div class="mb-3">
                        <h3 class="font-bold text-slate-800 text-sm flex items-center space-x-2">
                            <i data-lucide="grid" class="w-4 h-4 text-emerald-600"></i>
                            <span>Papan 100 Soal</span>
                        </h3>
                        <!-- Legend Status -->
                        <div class="grid grid-cols-3 gap-1 text-[10px] mt-2 text-slate-500 font-medium">
                            <div class="flex items-center space-x-1"><span class="w-2.5 h-2.5 rounded-full bg-emerald-600 inline-block"></span><span>Terjawab</span></div>
                            <div class="flex items-center space-x-1"><span class="w-2.5 h-2.5 rounded-full bg-amber-400 inline-block"></span><span>Ragu</span></div>
                            <div class="flex items-center space-x-1"><span class="w-2.5 h-2.5 rounded-full bg-slate-200 inline-block"></span><span>Kosong</span></div>
                        </div>
                    </div>

                    <!-- Scrollable Container untuk 100 Nomor -->
                    <div class="overflow-y-auto custom-scrollbar flex-1 pr-1 my-2">
                        <div class="grid grid-cols-5 gap-1.5" id="questionGrid">
                            <!-- Tombol 1 - 100 di-generate JS -->
                        </div>
                    </div>

                    <button onclick="submitQuiz()" class="w-full mt-3 bg-red-600 hover:bg-red-700 text-white font-semibold py-2.5 rounded-xl text-xs shadow transition flex items-center justify-center space-x-1">
                        <i data-lucide="check-circle" class="w-4 h-4"></i>
                        <span>Selesai & Kumpulkan</span>
                    </button>
                </div>
            </div>
        </section>

        <!-- SCREEN 3: HASIL & PEMBAHASAN -->
        <section id="screenResult" class="hidden space-y-6 max-w-4xl mx-auto">
            <!-- Card Skor -->
            <div class="bg-white rounded-2xl shadow-xl p-6 md:p-8 text-center border border-slate-200 relative overflow-hidden">
                <div class="absolute top-0 left-0 right-0 h-3 bg-emerald-600"></div>
                <h2 class="text-2xl font-bold text-slate-800 mb-1">Laporan Hasil Evaluasi AKG GTK</h2>
                <p class="text-slate-500 text-xs md:text-sm mb-6" id="resultUserDetail"></p>

                <div class="inline-flex flex-col items-center justify-center w-36 h-36 bg-emerald-50 rounded-full border-4 border-emerald-500 mb-6 shadow-inner">
                    <span class="text-[10px] text-slate-500 uppercase font-bold tracking-wider">Nilai Akhir</span>
                    <span class="text-4xl font-extrabold text-emerald-700" id="finalScore">0</span>
                    <span class="text-[10px] text-slate-400">Skala 0-100</span>
                </div>

                <div class="grid grid-cols-3 gap-3 max-w-md mx-auto mb-6">
                    <div class="bg-slate-50 p-3 rounded-xl border border-slate-200">
                        <p class="text-[11px] text-slate-500 font-medium">Total Soal</p>
                        <p class="text-lg font-bold text-slate-700">100</p>
                    </div>
                    <div class="bg-emerald-50 p-3 rounded-xl border border-emerald-200">
                        <p class="text-[11px] text-emerald-600 font-medium">Benar</p>
                        <p class="text-lg font-bold text-emerald-700" id="correctCount">0</p>
                    </div>
                    <div class="bg-red-50 p-3 rounded-xl border border-red-200">
                        <p class="text-[11px] text-red-600 font-medium">Salah / Kosong</p>
                        <p class="text-lg font-bold text-red-700" id="wrongCount">0</p>
                    </div>
                </div>

                <button onclick="restartQuiz()" class="bg-emerald-600 hover:bg-emerald-700 text-white font-semibold px-6 py-2.5 rounded-xl shadow transition inline-flex items-center space-x-2 text-sm">
                    <i data-lucide="rotate-ccw" class="w-4 h-4"></i>
                    <span>Coba Ujian Lainnya</span>
                </button>
            </div>

            <!-- Pembahasan Soal -->
            <div class="bg-white rounded-2xl shadow-xl p-6 md:p-8 border border-slate-200">
                <div class="flex flex-wrap justify-between items-center mb-6 pb-4 border-b gap-3">
                    <h3 class="text-xl font-bold text-slate-800 flex items-center space-x-2">
                        <i data-lucide="file-text" class="w-5 h-5 text-emerald-600"></i>
                        <span>Pembahasan 100 Soal</span>
                    </h3>
                    <div class="flex space-x-2">
                        <button onclick="filterPembahasan('all')" class="px-3 py-1.5 text-xs rounded-lg font-medium border bg-emerald-600 text-white">Semua (100)</button>
                        <button onclick="filterPembahasan('wrong')" class="px-3 py-1.5 text-xs rounded-lg font-medium border bg-slate-100 text-slate-600 hover:bg-slate-200">Hanya Salah</button>
                    </div>
                </div>

                <div id="pembahasanContainer" class="space-y-4">
                    <!-- List Pembahasan 100 Soal di-generate JS -->
                </div>
            </div>
        </section>

    </main>

    <!-- LOGIK JAVASCRIPT -->
    <script>
        // ==========================================
        // 1. DATA MASTER & GENERATOR 100 SOAL
        // ==========================================
        
        // Sampel Bank Soal Curated per Mapel & Jenjang
        const curatedQuestions = {
            "Al-Qur'an Hadis": {
                "MTs": [
                    { id: 1, soal: "Kedudukan Tajwid dalam membaca Al-Qur'an adalah fardhu 'ain. Ketika bertemu hukum Izhar Halqi, cara membacanya adalah...", pilihan: ["A. Mendengung 2 harakat", "B. Jelas tanpa dengung", "C. Memasukkan ke huruf berikutnya", "D. Membalikkan suara menjadi mim"], kunci: "B", pembahasan: "Izhar Halqi secara bahasa artinya jelas. Secara istilah membunyikan huruf nun mati/tanwin sesuai makhrajnya tanpa disertai dengung (ghunnah)." },
                    { id: 2, soal: "Suatu hadis yang diriwayatkan oleh banyak perawi pada setiap tingkatan sanadnya sehingga mustahil mereka sepakat berbuat dusta disebut...", pilihan: ["A. Hadis Ahad", "B. Hadis Hasan", "C. Hadis Mutawatir", "D. Hadis Gharib"], kunci: "C", pembahasan: "Hadis Mutawatir adalah hadis yang diriwayatkan oleh sejumlah besar perawi pada tiap tingkatan sanad yang menurut adat mustahil mereka sepakat berbuat bohong." },
                    { id: 3, soal: "Syarat utama perawi hadis dianggap 'Dhabit' adalah...", pilihan: ["A. Memiliki ingatan/hafalan yang sangat kuat dan akurat", "B. Beragama Islam dan baligh", "C. Menjaga harga diri (muru'ah)", "D. Memiliki banyak murid"], kunci: "A", pembahasan: "Dhabit artinya memiliki daya ingat/hafalan yang kuat serta akurat baik secara hafalan dada maupun catatan tulisan." }
                ],
                "MA": [
                    { id: 1, soal: "Dalam ilmu Musthalah Hadis, jika sanad suatu hadis gugur pada tingkat sahabat (tabi'in langsung menyebut Rasulullah), maka dinamakan...", pilihan: ["A. Hadis Mu'allaq", "B. Hadis Mursal", "C. Hadis Munqathi'", "D. Hadis Mu'dhal"], kunci: "B", pembahasan: "Hadis Mursal adalah hadis yang gugur sanadnya di tingkat sahabat." },
                    { id: 2, soal: "Kaidah 'Al-Ibratu bi 'umumin lafzi laa bi khushushi as-sabab' mengandung pengertian bahwa...", pilihan: ["A. Pegangan hukum adalah kekhususan sebab", "B. Pegangan hukum adalah keumuman lafaz, bukan kekhususan sebab", "C. Sebab nuzul membatasi hukum ayat selamanya", "D. Ayat umum tidak dapat ditakhsish"], kunci: "B", pembahasan: "Kaidah ini menetapkan bahwa ayat Al-Qur'an berlaku umum sesuai keumuman lafaznya." }
                ]
            }
        };

        // Fungsi Generator untuk melengkapi soal menjadi Tepat 100 Soal per Mapel
        function generate100Questions(mapel, jenjang) {
            let list = [];
            
            // Ambil soal kurasi jika ada
            if (curatedQuestions[mapel] && curatedQuestions[mapel][jenjang]) {
                list = [...curatedQuestions[mapel][jenjang]];
            }

            // Lengkapi sisa hingga 100 soal
            const startNumber = list.length + 1;
            for (let i = startNumber; i <= 100; i++) {
                list.push({
                    id: i,
                    soal: `[Soal No. ${i} - AKG GTK ${mapel} ${jenjang}] Soal uji kompetensi pedagogik dan profesionalisme guru mata pelajaran ${mapel} tingkat ${jenjang}. Bagaimanakah pendekatan strategi pembelajaran dan pemahaman materi yang paling tepat?`,
                    pilihan: [
                        `A. Menerapkan metode eksplorasi konsep dasar kompetensi ${mapel} secara sistematis.`,
                        `B. Mengutamakan hafalan tanpa analisis studi kasus terintegrasi.`,
                        `C. Menggunakan pendekatan monoton tanpa variasi media pembelajaran modern.`,
                        `D. Menyerahkan seluruh materi kepada peserta didik tanpa bimbingan guru.`
                    ],
                    kunci: "A",
                    pembahasan: `Pembahasan Soal No. ${i}: Dalam asesmen kompetensi guru (AKG), pendekatan profesionalisme dan pedagogik yang ideal pada mata pelajaran ${mapel} ${jenjang} memprioritaskan pemahaman konsep dasar, analisis kritis, dan metode pengajaran berpusat pada siswa.`
                });
            }

            return list;
        }

        // ==========================================
        // 2. STATE APLIKASI & TIMER
        // ==========================================
        let currentUser = { nama: "", jenjang: "", mapel: "" };
        let activeQuestions = [];
        let userAnswers = {}; // { qIndex: optIndex }
        let doubtFlags = {};  // { qIndex: true/false }
        let currentQIndex = 0;
        let timerInterval = null;
        let timeRemaining = 120 * 60; // 120 Menit dalam detik

        document.addEventListener('DOMContentLoaded', () => {
            lucide.createIcons();
        });

        // ==========================================
        // 3. REGISTRASI & TIMER LOGIC
        // ==========================================
        function handleStartQuiz(e) {
            e.preventDefault();
            const nama = document.getElementById('inputNama').value.trim();
            const jenjang = document.getElementById('selectJenjang').value;
            const mapel = document.getElementById('selectMapel').value;

            if (!nama || !jenjang || !mapel) {
                alert("Mohon lengkapi seluruh form registrasi.");
                return;
            }

            currentUser = { nama, jenjang, mapel };
            activeQuestions = generate100Questions(mapel, jenjang);

            // Reset state
            userAnswers = {};
            doubtFlags = {};
            currentQIndex = 0;
            timeRemaining = 120 * 60;

            // UI Header
            document.getElementById('badgeNama').textContent = currentUser.nama;
            document.getElementById('badgeMapel').textContent = currentUser.mapel;
            document.getElementById('badgeJenjang').textContent = currentUser.jenjang;
            document.getElementById('headerQuizInfo').classList.remove('hidden');

            // Switch Screen
            document.getElementById('screenRegister').classList.add('hidden');
            document.getElementById('screenQuiz').classList.remove('hidden');

            // Start Timer & Render
            startTimer();
            renderGrid();
            renderQuestion();
        }

        function startTimer() {
            clearInterval(timerInterval);
            timerInterval = setInterval(() => {
                timeRemaining--;
                if (timeRemaining <= 0) {
                    clearInterval(timerInterval);
                    alert("Waktu ujian telah habis! Jawaban Anda akan otomatis dikumpulkan.");
                    submitQuiz();
                    return;
                }

                const hours = Math.floor(timeRemaining / 3600);
                const minutes = Math.floor((timeRemaining % 3600) / 60);
                const seconds = timeRemaining % 60;

                const pad = (n) => n.toString().padStart(2, '0');
                document.getElementById('timerDisplay').textContent = `${pad(hours)}:${pad(minutes)}:${pad(seconds)}`;
            }, 1000);
        }

        // ==========================================
        // 4. CBT ENGINE & NAVIGASI 100 SOAL
        // ==========================================
        function renderGrid() {
            const grid = document.getElementById('questionGrid');
            grid.innerHTML = "";

            activeQuestions.forEach((_, idx) => {
                const btn = document.createElement('button');
                btn.type = "button";
                btn.textContent = idx + 1;
                btn.onclick = () => jumpToQuestion(idx);

                const isCurrent = idx === currentQIndex;
                const isAnswered = userAnswers[idx] !== undefined;
                const isDoubt = doubtFlags[idx] === true;

                let classes = "w-full h-8 rounded-lg text-xs font-bold border transition flex items-center justify-center ";

                if (isCurrent) {
                    classes += "ring-2 ring-emerald-600 border-emerald-600 bg-emerald-100 text-emerald-900 ";
                } else if (isDoubt) {
                    classes += "bg-amber-400 text-amber-950 border-amber-500 ";
                } else if (isAnswered) {
                    classes += "bg-emerald-600 text-white border-emerald-600 ";
                } else {
                    classes += "bg-slate-100 text-slate-600 border-slate-200 hover:bg-slate-200 ";
                }

                btn.className = classes;
                grid.appendChild(btn);
            });

            // Update statistik progres
            const answeredTotal = Object.keys(userAnswers).length;
            document.getElementById('answeredCount').textContent = answeredTotal;
            document.getElementById('progressBar').style.width = `${(answeredTotal / 100) * 100}%`;
        }

        function renderQuestion() {
            const q = activeQuestions[currentQIndex];
            document.getElementById('quizHeaderInfo').textContent = `Soal No. ${currentQIndex + 1} dari 100`;
            document.getElementById('questionText').textContent = q.soal;

            // Flag Ragu
            const isDoubt = doubtFlags[currentQIndex] === true;
            document.getElementById('flagBadge').classList.toggle('hidden', !isDoubt);
            
            const btnDoubt = document.getElementById('btnDoubt');
            if (isDoubt) {
                btnDoubt.className = "px-4 py-2.5 bg-amber-500 text-white font-medium rounded-xl text-xs md:text-sm flex items-center space-x-1.5 shadow transition";
            } else {
                btnDoubt.className = "px-4 py-2.5 bg-amber-100 hover:bg-amber-200 text-amber-800 font-medium rounded-xl text-xs md:text-sm flex items-center space-x-1.5 border border-amber-300 transition";
            }

            // Options
            const container = document.getElementById('optionsContainer');
            container.innerHTML = "";

            q.pilihan.forEach((optText, optIdx) => {
                const isSelected = userAnswers[currentQIndex] === optIdx;

                const card = document.createElement('div');
                card.onclick = () => selectOption(optIdx);
                card.className = `p-3.5 md:p-4 rounded-xl border-2 cursor-pointer transition flex items-center justify-between ${
                    isSelected 
                    ? "border-emerald-600 bg-emerald-50/80 text-emerald-900 font-medium" 
                    : "border-slate-200 hover:border-slate-300 bg-white text-slate-700"
                }`;

                card.innerHTML = `
                    <div class="flex items-center space-x-3 text-sm md:text-base">
                        <div class="w-6 h-6 rounded-full border-2 flex items-center justify-center text-xs font-bold shrink-0 ${
                            isSelected ? "border-emerald-600 bg-emerald-600 text-white" : "border-slate-400 text-slate-500"
                        }">
                            ${String.fromCharCode(65 + optIdx)}
                        </div>
                        <span>${optText}</span>
                    </div>
                `;
                container.appendChild(card);
            });

            // Nav State
            document.getElementById('btnPrev').disabled = currentQIndex === 0;
            document.getElementById('btnNext').disabled = currentQIndex === activeQuestions.length - 1;

            document.getElementById('btnPrev').classList.toggle('opacity-50', currentQIndex === 0);
            document.getElementById('btnNext').classList.toggle('opacity-50', currentQIndex === activeQuestions.length - 1);

            renderGrid();
        }

        function selectOption(optIdx) {
            userAnswers[currentQIndex] = optIdx;
            renderQuestion();
        }

        function toggleDoubt() {
            doubtFlags[currentQIndex] = !doubtFlags[currentQIndex];
            renderQuestion();
        }

        function jumpToQuestion(idx) {
            currentQIndex = idx;
            renderQuestion();
        }

        function navigateQuestion(dir) {
            const newIndex = currentQIndex + dir;
            if (newIndex >= 0 && newIndex < activeQuestions.length) {
                currentQIndex = newIndex;
                renderQuestion();
            }
        }

        function randomQuestion() {
            let randIdx;
            do {
                randIdx = Math.floor(Math.random() * 100);
            } while (randIdx === currentQIndex);

            currentQIndex = randIdx;
            renderQuestion();
        }

        // ==========================================
        // 5. EVALUASI HASIL & PEMBAHASAN
        // ==========================================
        function submitQuiz() {
            const answeredTotal = Object.keys(userAnswers).length;
            if (answeredTotal < 100) {
                const confirmSubmit = confirm(`Ustadz/Ustadzah baru menjawab ${answeredTotal} dari 100 soal. Yakin ingin menyelesaikan ujian?`);
                if (!confirmSubmit) return;
            }

            clearInterval(timerInterval);

            let correctCount = 0;
            activeQuestions.forEach((q, idx) => {
                const userChoice = userAnswers[idx];
                const keyIndex = q.kunci.charCodeAt(0) - 65;
                if (userChoice === keyIndex) {
                    correctCount++;
                }
            });

            const wrongCount = 100 - correctCount;
            const score = correctCount; // Karena 100 soal, 1 soal = 1 poin

            // Update UI Hasil
            document.getElementById('finalScore').textContent = score;
            document.getElementById('correctCount').textContent = correctCount;
            document.getElementById('wrongCount').textContent = wrongCount;
            document.getElementById('resultUserDetail').textContent = `${currentUser.nama} | Mapel: ${currentUser.mapel} (${currentUser.jenjang})`;

            // Render Pembahasan
            renderPembahasan('all');

            // Switch Screen
            document.getElementById('screenQuiz').classList.add('hidden');
            document.getElementById('headerQuizInfo').classList.add('hidden');
            document.getElementById('screenResult').classList.remove('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function renderPembahasan(filter) {
            const container = document.getElementById('pembahasanContainer');
            container.innerHTML = "";

            activeQuestions.forEach((q, idx) => {
                const userChoice = userAnswers[idx];
                const keyIndex = q.kunci.charCodeAt(0) - 65;
                const isCorrect = userChoice === keyIndex;

                if (filter === 'wrong' && isCorrect) return;

                const userText = userChoice !== undefined ? q.pilihan[userChoice] : "Tidak Dijawab";
                const keyText = q.pilihan[keyIndex];

                const card = document.createElement('div');
                card.className = `border rounded-2xl p-4 md:p-5 space-y-2.5 ${isCorrect ? "bg-emerald-50/40 border-emerald-200" : "bg-red-50/40 border-red-200"}`;

                card.innerHTML = `
                    <div class="flex items-center justify-between gap-2">
                        <span class="font-bold text-xs px-2.5 py-1 rounded-full ${isCorrect ? "bg-emerald-200 text-emerald-800" : "bg-red-200 text-red-800"}">
                            Soal No. ${idx + 1} - ${isCorrect ? "BENAR" : "SALAH / KOSONG"}
                        </span>
                    </div>

                    <p class="font-medium text-slate-800 text-sm md:text-base">${q.soal}</p>

                    <div class="grid grid-cols-1 md:grid-cols-2 gap-2 text-xs pt-2 border-t border-slate-200/60">
                        <div>
                            <span class="text-slate-500">Jawaban Peserta:</span>
                            <p class="font-semibold ${isCorrect ? "text-emerald-700" : "text-red-600"}">${userText}</p>
                        </div>
                        <div>
                            <span class="text-slate-500">Kunci Jawaban:</span>
                            <p class="font-semibold text-emerald-700">${keyText}</p>
                        </div>
                    </div>

                    <div class="bg-white p-3 md:p-4 rounded-xl border text-xs text-slate-700 space-y-1">
                        <span class="font-bold text-emerald-800 block flex items-center gap-1">
                            <i data-lucide="info" class="w-3.5 h-3.5 inline"></i> Pembahasan:
                        </span>
                        <p class="leading-relaxed">${q.pembahasan}</p>
                    </div>
                `;

                container.appendChild(card);
            });

            lucide.createIcons();
        }

        function filterPembahasan(type) {
            renderPembahasan(type);
        }

        function restartQuiz() {
            document.getElementById('screenResult').classList.add('hidden');
            document.getElementById('screenRegister').classList.remove('hidden');
            document.getElementById('headerQuizInfo').classList.add('hidden');
            document.getElementById('formStart').reset();
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
    </script>
</body>
</html>


function sendToWhatsApp() {
    // 1. Masukkan nomor WhatsApp Admin/Pengawas (Ganti dengan nomor Anda, gunakan format 62)
    const adminWANumber = "6281234567890"; // Contoh: 6281234567890 (Jangan pakai + atau 08)

    // 2. Ambil data hasil ujian
    const score = document.getElementById('finalScore').textContent;
    const correct = document.getElementById('correctCount').textContent;
    const wrong = document.getElementById('wrongCount').textContent;

    // 3. Buat format pesan teks WhatsApp
    const message = `*LAPORAN HASIL SIMULASI CBT AKG GTK KEMENAG*\n` +
        `----------------------------------------\n` +
        `👤 *Nama Peserta:* ${currentUser.nama}\n` +
        `🏫 *Satuan Pendidikan:* ${currentUser.jenjang}\n` +
        `📚 *Mata Pelajaran:* ${currentUser.mapel}\n` +
        `----------------------------------------\n` +
        `📊 *RINGKASAN NILAI:*\n` +
        `• *Nilai Akhir:* ${score} / 100\n` +
        `• *Jawaban Benar:* ${correct} soal\n` +
        `• *Jawaban Salah/Kosong:* ${wrong} soal\n` +
        `----------------------------------------\n` +
        `_Dikerjakan melalui Sistem Ujian CBT AKG Online_`;

    // 4. Encode URL agar karakter khusus & spasi terbaca di WA
    const encodedMessage = encodeURIComponent(message);

    // 5. Opsi Pengiriman:
    // A. Jika ingin langsung ke nomor Admin tertentu:
    const waURL = `https://wa.me/${adminWANumber}?text=${encodedMessage}`;
    
    // B. Jika ingin peserta memilih sendiri tujuan kontak WA-nya, gunakan line di bawah:
    // const waURL = `https://api.whatsapp.com/send?text=${encodedMessage}`;

    // Buka WhatsApp di tab baru / aplikasi WA
    window.open(waURL, '_blank');
}
