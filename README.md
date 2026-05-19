<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perolehan Hafalan Siswa - SMP Hamalatul Quran</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.29/jspdf.plugin.autotable.min.js"></script>
</head>
<body class="bg-gray-50 font-sans min-h-screen text-gray-800">

    <div class="container mx-auto px-4 py-8 max-w-7xl">
        <header class="text-center mb-8 bg-emerald-700 text-white p-6 rounded-2xl shadow-md">
            <h1 class="text-2xl md:text-3xl font-bold tracking-wide">PEROLEHAN HAFALAN SISWA</h1>
            <p class="text-emerald-100 text-sm md:text-base mt-1 font-medium">SMP Hamalatul Quran Ringinagung</p>
        </header>

        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
            <div class="bg-white p-6 rounded-2xl shadow-sm border border-gray-100 h-fit">
                <h2 class="text-xl font-semibold mb-4 text-emerald-800 border-b pb-2 flex items-center gap-2">
                    <span>📝</span> Input Data Hafalan
                </h2>
                <form id="hafalanForm" class="space-y-4">
                    <div class="grid grid-cols-3 gap-3">
                        <div class="col-span-2">
                            <label class="block text-xs font-bold text-gray-600 uppercase mb-1">Nama Siswa</label>
                            <input type="text" id="nama" required class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-emerald-500 text-sm" placeholder="Nama siswa">
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-gray-600 uppercase mb-1">Kelas</label>
                            <select id="kelas" class="w-full px-3 py-2 border rounded-lg bg-white focus:outline-none focus:ring-2 focus:ring-emerald-500 text-sm">
                                <option value="7">7</option>
                                <option value="8">8</option>
                                <option value="9">9</option>
                            </select>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 gap-3">
                        <div>
                            <label class="block text-xs font-bold text-gray-600 uppercase mb-1">Awal Setoran</label>
                            <input type="text" id="awalSetoran" required class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-emerald-500 text-sm" placeholder="Contoh: An-Nas 1">
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-gray-600 uppercase mb-1">Akhir Setoran</label>
                            <input type="text" id="akhirSetoran" required class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-emerald-500 text-sm" placeholder="Contoh: Al-Humazah 5">
                        </div>
                    </div>

                    <div class="grid grid-cols-2 gap-3">
                        <div>
                            <label class="block text-xs font-bold text-gray-600 uppercase mb-1">Minggu Ini</label>
                            <input type="text" id="mingguIni" required class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-emerald-500 text-sm" placeholder="Contoh: 1/2 Juz">
                        </div>
                        <div>
                            <label class="block text-xs font-bold text-gray-600 uppercase mb-1">Total Perolehan</label>
                            <input type="text" id="totalPerolehan" required class="w-full px-3 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-emerald-500 text-sm" placeholder="Contoh: 3 Juz">
                        </div>
                    </div>

                    <div>
                        <label class="block text-xs font-bold text-gray-600 uppercase mb-1">Status Hafalan</label>
                        <select id="statusHafalan" class="w-full px-3 py-2 border rounded-lg bg-white focus:outline-none focus:ring-2 focus:ring-emerald-500 text-sm">
                            <option value="Iqro">Iqro</option>
                            <option value="Binnadzor">Binnadzor</option>
                            <option value="Ziyadah" selected>Ziyadah</option>
                            <option value="Murojaah 1">Murojaah 1</option>
                            <option value="Murojaah 2">Murojaah 2</option>
                            <option value="Murojaah 3">Murojaah 3</option>
                            <option value="Dauroh Tasmik">Dauroh Tasmik</option>
                        </select>
                    </div>

                    <div>
                        <label class="block text-xs font-bold text-gray-600 uppercase mb-1">Guru Pengampu / Penyimak</label>
                        <select id="guru" required class="w-full px-3 py-2 border rounded-lg bg-white focus:outline-none focus:ring-2 focus:ring-emerald-500 text-sm">
                            <option value="" disabled selected hidden>Pilih nama guru di sini...</option>
                            <option value="Kholifatus Sholihah al-auliya">Kholifatus Sholihah al-auliya</option>
                            <option value="Redita Anisya">Redita Anisya</option>
                            <option value="Anggita May Anggraini">Anggita May Anggraini</option>
                            <option value="Siti Nur Hasanah">Siti Nur Hasanah</option>
                            <option value="Ratu Bilqish">Ratu Bilqish</option>
                            <option value="Hafidhoh Sidqiyah">Hafidhoh Sidqiyah</option>
                        </select>
                    </div>

                    <div class="grid grid-cols-2 gap-3 mt-2">
                        <button type="button" id="resetFormBtn" class="bg-gray-200 hover:bg-gray-300 text-gray-700 font-semibold py-2.5 rounded-lg transition text-sm cursor-pointer">
                            🔄 Reset Form
                        </button>
                        <button type="submit" class="bg-emerald-600 hover:bg-emerald-700 text-white font-semibold py-2.5 rounded-lg transition text-sm shadow-sm cursor-pointer">
                            💾 Simpan Data
                        </button>
                    </div>
                </form>
            </div>

            <div class="lg:col-span-2 bg-white p-6 rounded-2xl shadow-sm border border-gray-100 flex flex-col justify-between">
                <div>
                    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3 mb-4 border-b pb-2">
                        <h2 class="text-xl font-semibold text-emerald-800 flex items-center gap-2">
                            <span>📊</span> Tabel Rekapitulasi
                        </h2>
                        <button id="downloadPdfBtn" class="bg-red-600 hover:bg-red-700 text-white font-medium px-4 py-1.5 rounded-lg text-xs transition flex items-center gap-1.5 shadow-sm cursor-pointer">
                            📄 Download PDF
                        </button>
                    </div>

                    <div class="overflow-x-auto">
                        <table class="w-full text-left border-collapse text-sm">
                            <thead>
                                <tr class="bg-gray-100 text-gray-700 uppercase text-xs tracking-wider border-b border-gray-200">
                                    <th class="py-3 px-4 font-bold text-center">No</th>
                                    <th class="py-3 px-4 font-bold">Nama</th>
                                    <th class="py-3 px-4 font-bold text-center">Kelas</th>
                                    <th class="py-3 px-4 font-bold">Awal</th>
                                    <th class="py-3 px-4 font-bold">Akhir</th>
                                    <th class="py-3 px-4 font-bold text-center">Minggu Ini</th>
                                    <th class="py-3 px-4 font-bold text-center">Total</th>
                                    <th class="py-3 px-4 font-bold text-center">Status</th>
                                    <th class="py-3 px-4 font-bold">Guru</th>
                                    <th class="py-3 px-4 font-bold text-center">Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="tabelBody" class="divide-y divide-gray-100">
                                </tbody>
                        </table>
                        <div id="emptyState" class="text-center py-12 text-gray-400 text-sm">
                            Belum ada data setoran hafalan yang disimpan.
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Array penampung data (Tabel dimulai dari kosong)
        let dataHafalan = [];

        const form = document.getElementById('hafalanForm');
        const tabelBody = document.getElementById('tabelBody');
        const emptyState = document.getElementById('emptyState');
        const downloadPdfBtn = document.getElementById('downloadPdfBtn');
        const resetFormBtn = document.getElementById('resetFormBtn');

        // Fungsi memperbarui tampilan tabel
        function updateTable() {
            tabelBody.innerHTML = '';
            
            if (dataHafalan.length === 0) {
                emptyState.classList.remove('hidden');
            } else {
                emptyState.classList.add('hidden');
                
                dataHafalan.forEach((item, index) => {
                    // Warna badge dinamis berdasarkan status
                    let statusColor = 'bg-gray-100 text-gray-700';
                    if(item.status === 'Ziyadah') statusColor = 'bg-blue-100 text-blue-700';
                    else if(item.status.includes('Murojaah')) statusColor = 'bg-amber-100 text-amber-700';
                    else if(item.status === 'Dauroh Tasmik') statusColor = 'bg-purple-100 text-purple-700';
                    else if(item.status === 'Iqro') statusColor = 'bg-rose-100 text-rose-700';

                    const row = `
                        <tr class="hover:bg-gray-50/70 transition">
                            <td class="py-3 px-4 text-center font-medium text-gray-500">${index + 1}</td>
                            <td class="py-3 px-4 font-semibold text-gray-900">${item.nama}</td>
                            <td class="py-3 px-4 text-center text-gray-700 font-medium">Kelas ${item.kelas}</td>
                            <td class="py-3 px-4 text-gray-600">${item.awal}</td>
                            <td class="py-3 px-4 text-gray-600">${item.akhir}</td>
                            <td class="py-3 px-4 text-center font-medium text-emerald-600">${item.mingguIni}</td>
                            <td class="py-3 px-4 text-center font-bold text-gray-800">${item.total}</td>
                            <td class="py-3 px-4 text-center">
                                <span class="px-2.5 py-1 rounded-full text-xs font-semibold ${statusColor}">${item.status}</span>
                            </td>
                            <td class="py-3 px-4 text-gray-700 font-medium">${item.guru}</td>
                            <td class="py-3 px-4 text-center">
                                <button onclick="hapusData(${index})" class="text-rose-500 hover:text-rose-700 font-medium text-xs transition cursor-pointer">Hapus</button>
                            </td>
                        </tr>
                    `;
                    tabelBody.insertAdjacentHTML('beforeend', row);
                });
            }
        }

        // Jalankan fungsi table pertama kali
        updateTable();

        // Event saat tombol Simpan ditekan
        form.addEventListener('submit', function(e) {
            e.preventDefault();

            const nama = document.getElementById('nama').value;
            const kelas = document.getElementById('kelas').value;
            const awal = document.getElementById('awalSetoran').value;
            const akhir = document.getElementById('akhirSetoran').value;
            const mingguIni = document.getElementById('mingguIni').value;
            const total = document.getElementById('totalPerolehan').value;
            const status = document.getElementById('statusHafalan').value;
            const guru = document.getElementById('guru').value; // Ambil nama guru dari dropdown

            // Masukkan data ke array
            dataHafalan.push({ nama, kelas, awal, akhir, mingguIni, total, status, guru });

            // Refresh tabel & reset form bawaan
            updateTable();
            form.reset();
            document.getElementById('nama').focus();
        });

        // Event saat tombol Reset Form ditekan manual
        resetFormBtn.addEventListener('click', function() {
            if(confirm("Apakah Anda yakin ingin mengosongkan form input ini?")) {
                form.reset();
            }
        });

        // Fungsi menghapus baris data
        function hapusData(index) {
            if(confirm("Apakah Anda yakin ingin menghapus data ini?")) {
                dataHafalan.splice(index, 1);
                updateTable();
            }
        }

        // Fitur Download PDF menggunakan jsPDF & jsPDF-AutoTable
        downloadPdfBtn.addEventListener('click', function() {
            if(dataHafalan.length === 0) {
                alert("Tidak ada data untuk didownload!");
                return;
            }

            const { jsPDF } = window.jspdf;
            const doc = new jsPDF('l', 'mm', 'a4');

            // Judul Dokumen PDF
            doc.setFont("Helvetica", "bold");
            doc.setFontSize(16);
            doc.text("LAPORAN PEROLEHAN HAFALAN SISWA", 148, 15, { align: "center" });
            
            doc.setFontSize(12);
            doc.setFont("Helvetica", "normal");
            doc.text("SMP Hamalatul Quran Ringinagung", 148, 21, { align: "center" });
            
            // Tanggal Otomatis di lembar PDF
            const opsiTanggal = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            const tanggalSekarang = new Date().toLocaleDateString('id-ID', opsiTanggal);
            doc.setFontSize(10);
            doc.setFont("Helvetica", "italic");
            doc.text("Dicetak pada: " + tanggalSekarang, 15, 27);

            // Garis pembatas
            doc.setLineWidth(0.5);
            doc.setDrawColor(16, 185, 129);
            doc.line(15, 29, 282, 29);

            // Menyiapkan data untuk tabel PDF
            const bodyData = dataHafalan.map((item, idx) => [
                idx + 1,
                item.nama,
                "Kelas " + item.kelas,
                item.awal,
                item.akhir,
                item.mingguIni,
                item.total,
                item.status,
                item.guru
            ]);

            // Membuat tabel otomatis di PDF
            doc.autoTable({
                startY: 34,
                head: [['No', 'Nama Siswa', 'Kelas', 'Awal Setoran', 'Akhir Setoran', 'Perolehan Minggu Ini', 'Total Seluruhnya', 'Status Hafalan', 'Guru Pengampu']],
                body: bodyData,
                theme: 'striped',
                headStyles: { fillColor: [16, 124, 65], halign: 'center' },
                columnStyles: {
                    0: { halign: 'center', cellWidth: 12 },
                    1: { fontStyle: 'bold' },
                    2: { halign: 'center', cellWidth: 20 },
                    5: { halign: 'center' },
                    6: { halign: 'center', fontStyle: 'bold' },
                    7: { halign: 'center' },
                    8: { fontStyle: 'normal' }
                },
                styles: { fontSize: 10, cellPadding: 3 }
            });

            // Download file PDF hasil generate
            doc.save("Rekap_Hafalan_SMP_HQ_Ringinagung.pdf");
        });
    </script>
</body>
</html>
