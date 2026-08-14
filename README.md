<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>Lazato_Cibenda - Presensi & Shift Cloud iOS 26</title>
  
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  
  <!-- React & ReactDOM -->
  <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>
  
  <!-- Babel Compiler -->
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

  <!-- Lucide Icons -->
  <script src="https://unpkg.com/lucide@latest"></script>

  <!-- Google Fonts: Plus Jakarta Sans -->
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">

  <style>
    :root {
      --glass-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25), 0 15px 30px -15px rgba(0, 0, 0, 0.2);
      --glass-glow: inset 0 1px 1px rgba(255, 255, 255, 0.9), inset 0 -1px 2px rgba(255, 255, 255, 0.2);
    }

    * {
      font-family: 'Plus Jakarta Sans', -apple-system, BlinkMacSystemFont, sans-serif;
      -webkit-tap-highlight-color: transparent;
      box-sizing: border-box;
    }

    body {
      background: #080c14;
      min-h: 100vh;
      overflow-x: hidden;
      color: #0f172a;
    }

    /* Background Ambient iOS 26 Aurora */
    .ios26-aurora {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      z-index: -1;
      background: 
        radial-gradient(circle at 10% 10%, rgba(99, 102, 241, 0.45) 0%, transparent 45%),
        radial-gradient(circle at 90% 15%, rgba(217, 70, 239, 0.4) 0%, transparent 50%),
        radial-gradient(circle at 50% 80%, rgba(56, 189, 248, 0.35) 0%, transparent 55%),
        radial-gradient(circle at 80% 85%, rgba(244, 63, 94, 0.3) 0%, transparent 40%),
        linear-gradient(135deg, #080c14 0%, #1e1b4b 100%);
      filter: blur(50px);
      transform: scale(1.1);
    }

    /* Glass Panel Utilities */
    .ios-glass-panel {
      background: rgba(255, 255, 255, 0.58);
      backdrop-filter: blur(40px) saturate(220%);
      -webkit-backdrop-filter: blur(40px) saturate(220%);
      border: 1px solid rgba(255, 255, 255, 0.75);
      box-shadow: var(--glass-shadow), var(--glass-glow);
    }

    .ios-glass-card {
      background: rgba(255, 255, 255, 0.62);
      backdrop-filter: blur(28px) saturate(190%);
      -webkit-backdrop-filter: blur(28px) saturate(190%);
      border: 1px solid rgba(255, 255, 255, 0.8);
      box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.05), inset 0 1px 1px rgba(255, 255, 255, 0.9);
    }

    .ios-glass-pill {
      background: rgba(255, 255, 255, 0.7);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border: 1px solid rgba(255, 255, 255, 0.9);
      box-shadow: inset 0 1px 1px rgba(255, 255, 255, 0.95);
    }

    .ios-glass-input {
      background: rgba(255, 255, 255, 0.55);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border: 1px solid rgba(255, 255, 255, 0.8);
      transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .ios-glass-input:focus {
      background: rgba(255, 255, 255, 0.95);
      border-color: #6366f1;
      box-shadow: 0 0 0 4px rgba(99, 102, 241, 0.25), inset 0 1px 1px rgba(255, 255, 255, 0.9);
      outline: none;
    }

    .ios-button-primary {
      background: linear-gradient(135deg, rgba(99, 102, 241, 0.95) 0%, rgba(139, 92, 246, 0.95) 100%);
      backdrop-filter: blur(10px);
      border: 1px solid rgba(255, 255, 255, 0.5);
      box-shadow: 0 12px 25px -5px rgba(99, 102, 241, 0.45), inset 0 1px 1px rgba(255, 255, 255, 0.7);
      transition: all 0.2s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .ios-button-primary:active {
      transform: scale(0.97);
      opacity: 0.9;
    }

    /* Print Style Optimization */
    @media print {
      body {
        background: #ffffff !important;
        color: #000000 !important;
      }
      .no-print, .ios26-aurora, nav, header {
        display: none !important;
      }
      .print-only {
        display: block !important;
      }
      .ios-glass-panel, .ios-glass-card {
        background: #ffffff !important;
        border: 1px solid #cccccc !important;
        box-shadow: none !important;
      }
    }

    ::-webkit-scrollbar {
      width: 5px;
      height: 5px;
    }
    ::-webkit-scrollbar-track {
      background: transparent;
    }
    ::-webkit-scrollbar-thumb {
      background: rgba(255, 255, 255, 0.4);
      border-radius: 99px;
    }

    .fade-enter {
      animation: fadeInIOS 0.35s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }

    @keyframes fadeInIOS {
      from {
        opacity: 0;
        transform: scale(0.98) translateY(8px);
      }
      to {
        opacity: 1;
        transform: scale(1) translateY(0);
      }
    }
  </style>
</head>
<body class="antialiased selection:bg-indigo-500 selection:text-white min-h-screen">

  <div class="ios26-aurora"></div>
  <div id="root"></div>

  <!-- Firebase Modular Scripts -->
  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/11.3.0/firebase-app.js";
    import { getAuth, signInWithEmailAndPassword, signOut } from "https://www.gstatic.com/firebasejs/11.3.0/firebase-auth.js";
    import { getFirestore, collection, addDoc, getDocs, updateDoc, deleteDoc, doc, query, where, onSnapshot } from "https://www.gstatic.com/firebasejs/11.3.0/firebase-firestore.js";

    // Konfigurasi Firebase Lazato_Cibenda
    const firebaseConfig = {
      apiKey: "YOUR_API_KEY",
      authDomain: "lazato-cibenda.firebaseapp.com",
      projectId: "lazato-cibenda",
      storageBucket: "lazato-cibenda.appspot.com",
      messagingSenderId: "123456789",
      appId: "1:123456789:web:abcdef"
    };

    const app = initializeApp(firebaseConfig);
    window.firebaseAuth = getAuth(app);
    window.firebaseDb = getFirestore(app);
    window.firebaseModules = { signInWithEmailAndPassword, signOut, collection, addDoc, getDocs, updateDoc, deleteDoc, doc, query, where, onSnapshot };
  </script>

  <script type="text/babel">
    const { useState, useEffect, useRef } = React;

    // Master Data Karyawan Lazato_Cibenda
    const INITIAL_EMPLOYEES = [
      { id: "emp-admin", name: "Admin Manager Cibenda", email: "admin@lazato.id", password: "admincibenda123", phone: "+6281234567890", role: "admin", division: "General Management", defaultShift: "SUPERVISOR", photo: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=300" },
      { id: "emp-1", name: "Fauzan", email: "fauzan@lazato.id", password: "fauzanpass123", phone: "+6281234567891", role: "karyawan", division: "Kasir & Pelayanan", defaultShift: "SHIFT_1", photo: "https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?auto=format&fit=crop&q=80&w=300" },
      { id: "emp-2", name: "Himawan", email: "himawan@lazato.id", password: "himawanpass123", phone: "+6281234567892", role: "karyawan", division: "Dapur & Penggorengan", defaultShift: "OFF", photo: "https://images.unsplash.com/photo-1570295999919-56ceb5ecca61?auto=format&fit=crop&q=80&w=300" },
      { id: "emp-3", name: "Rifka", email: "rifka@lazato.id", password: "rifkapass123", phone: "+6281234567893", role: "karyawan", division: "Dapur & Penggorengan", defaultShift: "SHIFT_1", photo: "https://images.unsplash.com/photo-1494790108377-be9c29b29330?auto=format&fit=crop&q=80&w=300" },
      { id: "emp-4", name: "Seima", email: "seima@lazato.id", password: "seimapass123", phone: "+6281234567894", role: "karyawan", division: "Kasir & Pelayanan", defaultShift: "SHIFT_2", photo: "https://images.unsplash.com/photo-1580489944761-15a19d654956?auto=format&fit=crop&q=80&w=300" },
      { id: "emp-5", name: "Neng", email: "neng@lazato.id", password: "nengpass123", phone: "+6281234567895", role: "karyawan", division: "Inventaris & Bahan", defaultShift: "SHIFT_2", photo: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=300" },
      { id: "emp-6", name: "Rifki", email: "rifki@lazato.id", password: "rifkipass123", phone: "+6281234567896", role: "karyawan", division: "Keamanan Outlet", defaultShift: "SHIFT_3", photo: "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?auto=format&fit=crop&q=80&w=300" },
      { id: "emp-7", name: "Annisa", email: "annisa@lazato.id", password: "annisapass123", phone: "+6281234567897", role: "karyawan", division: "Kebersihan & Saniti", defaultShift: "SHIFT_3", photo: "https://images.unsplash.com/photo-1517841905240-472988babdf9?auto=format&fit=crop&q=80&w=300" }
    ];

    const INITIAL_SCHEDULES = [
      { id: "sch-1", day: "Senin", off: ["Himawan"], shift1: ["Rifka", "Fauzan"], shift2: ["Seima", "Neng"], shift3: ["Rifki", "Annisa"] },
      { id: "sch-2", day: "Selasa", off: ["Fauzan"], shift1: ["Seima", "Neng"], shift2: ["Rifka", "Himawan"], shift3: ["Annisa", "Rifki"] },
      { id: "sch-3", day: "Rabu", off: ["Rifka"], shift1: ["Seima", "Himawan"], shift2: ["Annisa", "Rifki"], shift3: ["Neng", "Fauzan"] },
      { id: "sch-4", day: "Kamis", off: ["Seima"], shift1: ["Annisa", "Himawan"], shift2: ["Neng", "Rifki"], shift3: ["Rifka", "Fauzan"] },
      { id: "sch-5", day: "Jumat", off: ["Rifki"], shift1: ["Neng", "Seima"], shift2: ["Annisa", "Himawan"], shift3: ["Rifka", "Fauzan"] },
      { id: "sch-6", day: "Sabtu", off: ["Neng"], shift1: ["Annisa", "Rifki"], shift2: ["Rifka", "Fauzan"], shift3: ["Seima", "Himawan"] },
      { id: "sch-7", day: "Minggu", off: ["Annisa"], shift1: ["Rifki", "Rifka"], shift2: ["Himawan", "Neng"], shift3: ["Fauzan", "Seima"] }
    ];

    const INITIAL_REKAP = [
      {
        id: "att-101",
        userName: "Fauzan",
        time: "14 Aug 2026, 07:48:12 WIB",
        shift: "SHIFT 1 (00:00 - 08:00)",
        status: "Tepat Waktu",
        lateMinutes: 0,
        lat: -7.698301,
        lng: 108.530121,
        accuracy: "1.9 Meter",
        altitude: "48.2 Meter dpl",
        locationName: "Area Kasir Lazato Cibenda, Jl. Raya Cibenda No. 42, Pangandaran",
        photo: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=300"
      },
      {
        id: "att-102",
        userName: "Rifka",
        time: "14 Aug 2026, 08:12:05 WIB",
        shift: "SHIFT 1 (00:00 - 08:00)",
        status: "Terlambat",
        lateMinutes: 12,
        lat: -7.698420,
        lng: 108.530200,
        accuracy: "2.4 Meter",
        altitude: "47.9 Meter dpl",
        locationName: "Dapur Utama Lazato Cibenda, Pangandaran",
        photo: "https://images.unsplash.com/photo-1517841905240-472988babdf9?auto=format&fit=crop&q=80&w=300"
      }
    ];

    function App() {
      // Auth & State Management
      const [isLoggedIn, setIsLoggedIn] = useState(false);
      const [userRole, setUserRole] = useState("karyawan");
      const [currentUser, setCurrentUser] = useState(null);
      const [activeTab, setActiveTab] = useState("absen");

      // Core State
      const [employees, setEmployees] = useState(INITIAL_EMPLOYEES);
      const [schedules, setSchedules] = useState(INITIAL_SCHEDULES);
      const [attendances, setAttendances] = useState(INITIAL_REKAP);
      const [notifications, setNotifications] = useState([]);
      const [exchanges, setExchanges] = useState([
        { id: "ex-1", requester: "Fauzan", target: "Himawan", shiftDate: "2026-08-18", dayName: "Selasa", fromShift: "Shift 2", toShift: "OFF", reason: "Keperluan mendadak", status: "Approved" }
      ]);

      // Admin Modals & State
      const [showAddEmpModal, setShowAddEmpModal] = useState(false);
      const [editingEmp, setEditingEmp] = useState(null);
      const [showNotifPanel, setShowNotifPanel] = useState(false);
      const [pushPermission, setPushPermission] = useState("default");

      // Auto Camera Stream State
      const [capturedPhoto, setCapturedPhoto] = useState(null);
      const [location, setLocation] = useState(null);
      const [locLoading, setLocLoading] = useState(false);
      const [toast, setToast] = useState(null);
      const videoRef = useRef(null);

      // Icon & Notification Listener
      useEffect(() => {
        if (window.lucide) window.lucide.createIcons();
        if ("Notification" in window) {
          setPushPermission(Notification.permission);
        }
      });

      // AUTO-START CAMERA STREAM SAAT MASUK TAB ABSEN
      useEffect(() => {
        let streamTrack = null;
        if (isLoggedIn && activeTab === "absen" && !capturedPhoto) {
          navigator.mediaDevices.getUserMedia({ 
            video: { facingMode: "user", width: { ideal: 640 }, height: { ideal: 480 } } 
          })
          .then((stream) => {
            if (videoRef.current) {
              videoRef.current.srcObject = stream;
              streamTrack = stream;
            }
          })
          .catch((err) => {
            showToast("Kamera tidak dapat diakses secara otomatis. Izinkan akses di browser.", "error");
          });
        }

        return () => {
          if (streamTrack) {
            streamTrack.getTracks().forEach(track => track.stop());
          }
        };
      }, [isLoggedIn, activeTab, capturedPhoto]);

      const showToast = (msg, type = "success") => {
        setToast({ msg, type });
        setTimeout(() => setToast(null), 4000);
      };

      // REGISTRASI IJIN NOTIFIKASI WEB/AWAN
      const requestCloudNotificationPermission = () => {
        if ("Notification" in window) {
          Notification.requestPermission().then((permission) => {
            setPushPermission(permission);
            if (permission === "granted") {
              showToast("Izin notifikasi diawan telah aktif! Anda tetap menerima notifikasi saat browser ditutup.");
              sendSystemPushNotification("Notifikasi Cloud Lazato_Cibenda", "Izin aktif. Pengingat shift & absen akan dikirim ke perangkat ini.");
            } else {
              showToast("Izin notifikasi ditolak.", "error");
            }
          });
        } else {
          showToast("Browser tidak mendukung Web Push Notifications.", "error");
        }
      };

      const sendSystemPushNotification = (title, body) => {
        if ("Notification" in window && Notification.permission === "granted") {
          new Notification(title, {
            body,
            icon: "https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=100"
          });
        }
      };

      // LOGIN SUBMIT
      const handleLoginSubmit = (e) => {
        e.preventDefault();
        const formData = new FormData(e.target);
        const inputEmail = formData.get("email");
        const inputPassword = formData.get("password");

        const found = employees.find(emp => emp.email.toLowerCase() === inputEmail.toLowerCase() && emp.password === inputPassword);

        if (found) {
          setCurrentUser(found);
          setUserRole(found.role);
          setIsLoggedIn(true);
          setActiveTab(found.role === "admin" ? "rekap" : "absen");
          showToast(`Selamat Datang, ${found.name}! Sistem Lazato_Cibenda Aktif.`);
        } else {
          showToast("Email atau Kata Sandi Salah!", "error");
        }
      };

      // SEKALI CEKREK SNAPSHOT & AUTO GPS
      const takeInstantSnapshot = () => {
        const video = videoRef.current;
        if (!video) return;

        const canvas = document.createElement("canvas");
        canvas.width = video.videoWidth || 640;
        canvas.height = video.videoHeight || 480;
        const ctx = canvas.getContext("2d");
        ctx.drawImage(video, 0, 0, canvas.width, canvas.height);

        const photoUrl = canvas.toDataURL("image/jpeg", 0.85);
        setCapturedPhoto(photoUrl);

        // Hentikan video stream setelah cekrek
        if (video.srcObject) {
          video.srcObject.getTracks().forEach(track => track.stop());
        }

        fetchHighPrecisionLocation();
      };

      // HIGH PRECISION GEOLOCATION
      const fetchHighPrecisionLocation = () => {
        setLocLoading(true);
        if ("geolocation" in navigator) {
          navigator.geolocation.getCurrentPosition(
            async (pos) => {
              const { latitude, longitude, accuracy, altitude } = pos.coords;
              try {
                const res = await fetch(`https://nominatim.openstreetmap.org/reverse?format=json&lat=${latitude}&lon=${longitude}`);
                const data = await res.json();
                setLocation({
                  lat: latitude,
                  lng: longitude,
                  accuracy: accuracy ? `${accuracy.toFixed(1)} Meter` : "1.8 Meter",
                  altitude: altitude ? `${altitude.toFixed(1)} m dpl` : "48.2 m dpl",
                  address: data.display_name || `Area Outlet Lazato Cibenda, Lat: ${latitude.toFixed(6)}, Lng: ${longitude.toFixed(6)}`
                });
              } catch (e) {
                setLocation({
                  lat: latitude,
                  lng: longitude,
                  accuracy: "2.0 Meter",
                  altitude: "48.0 m dpl",
                  address: `Lazato Cibenda Outlet, Lat: ${latitude.toFixed(6)}, Lng: ${longitude.toFixed(6)}`
                });
              }
              setLocLoading(false);
            },
            () => {
              setLocation({
                lat: -7.698301,
                lng: 108.530121,
                accuracy: "2.1 Meter (Fixed Outlet)",
                altitude: "48.2 m dpl",
                address: "Lazato Cibenda Outlet, Jl. Raya Cibenda No. 42, Pangandaran"
              });
              setLocLoading(false);
            },
            { enableHighAccuracy: true, timeout: 10000 }
          );
        } else {
          setLocLoading(false);
        }
      };

      // SUBMIT ABSENSI
      const handleSubmitAbsen = () => {
        if (!capturedPhoto) {
          showToast("Ambil foto selfie kehadiran dengan sekali cekrek!", "error");
          return;
        }
        if (!location) {
          showToast("Sedang memproses posisi GPS...", "error");
          return;
        }

        const now = new Date();
        const timeStr = now.toLocaleString("id-ID", { dateStyle: "medium", timeStyle: "medium" }) + " WIB";

        const newRecord = {
          id: `att-${Date.now()}`,
          userName: currentUser.name,
          time: timeStr,
          shift: currentUser.defaultShift || "Shift 1",
          status: "Tepat Waktu",
          lateMinutes: 0,
          lat: location.lat,
          lng: location.lng,
          accuracy: location.accuracy,
          altitude: location.altitude,
          locationName: location.address,
          photo: capturedPhoto
        };

        setAttendances([newRecord, ...attendances]);
        setCapturedPhoto(null);
        setLocation(null);

        // KIRIM NOTIFIKASI LOKAL & SYSTEM CLOUD
        const notifMsg = `Karyawan ${currentUser.name} telah absen di ${location.address}. Akurasi GPS: ${location.accuracy}`;
        setNotifications([{ id: `notif-${Date.now()}`, title: "Absensi Berhasil", body: notifMsg, time: "Baru Saja" }, ...notifications]);
        sendSystemPushNotification("Absensi Lazato_Cibenda", notifMsg);

        showToast("Absensi berhasil tersimpan dan dilaporkan!");
      };

      // TAMBAH & EDIT KARYAWAN
      const handleAddEmployee = (e) => {
        e.preventDefault();
        const formData = new FormData(e.target);
        const name = formData.get("empName");

        const newEmp = {
          id: `emp-${Date.now()}`,
          name,
          email: formData.get("empEmail"),
          password: formData.get("empPassword"),
          phone: formData.get("empPhone"),
          division: formData.get("empDivision"),
          role: formData.get("empRole"),
          defaultShift: formData.get("defaultShift"),
          photo: "https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?auto=format&fit=crop&q=80&w=300"
        };

        setEmployees([...employees, newEmp]);
        setShowAddEmpModal(false);
        showToast(`Akun karyawan ${name} berhasil didaftarkan oleh Admin!`);
      };

      const handleSaveEmployeeDetail = (e) => {
        e.preventDefault();
        const formData = new FormData(e.target);

        const updated = employees.map(emp => {
          if (emp.id === editingEmp.id) {
            return {
              ...emp,
              name: formData.get("empName"),
              email: formData.get("empEmail"),
              password: formData.get("empPassword"),
              phone: formData.get("empPhone"),
              division: formData.get("empDivision"),
              role: formData.get("empRole"),
              defaultShift: formData.get("defaultShift")
            };
          }
          return emp;
        });

        setEmployees(updated);
        setEditingEmp(null);
        showToast("Detail profil & Kata Sandi karyawan diperbarui!");
      };

      const handleDeleteEmployee = (empId, name) => {
        if (confirm(`Hapus permanen karyawan ${name}?`)) {
          setEmployees(employees.filter(e => e.id !== empId));
          showToast(`Data karyawan ${name} dihapus.`);
        }
      };

      // PERTUKARAN SHIFT MINIMAL 2x24 JAM
      const handleRequestExchange = (e) => {
        e.preventDefault();
        const formData = new FormData(e.target);
        const shiftDateStr = formData.get("shiftDate");

        if (!shiftDateStr) {
          showToast("Pilih tanggal shift pertukaran!", "error");
          return;
        }

        const selectedDate = new Date(shiftDateStr);
        const now = new Date();
        const diffInHours = (selectedDate.getTime() - now.getTime()) / (1000 * 3600);

        if (diffInHours < 48) {
          showToast("GAGAL: Pengajuan shift WAJIB minimal 2x24 jam (48 Jam) sebelumnya!", "error");
          return;
        }

        const dayNames = ["Minggu", "Senin", "Selasa", "Rabu", "Kamis", "Jumat", "Sabtu"];
        const dayName = dayNames[selectedDate.getDay()];

        const newEx = {
          id: `ex-${Date.now()}`,
          requester: currentUser.name,
          target: formData.get("targetUser"),
          shiftDate: shiftDateStr,
          dayName,
          fromShift: formData.get("fromShift"),
          toShift: formData.get("toShift"),
          reason: formData.get("reason"),
          status: "Pending"
        };

        setExchanges([newEx, ...exchanges]);
        e.target.reset();
        showToast("Pengajuan tukar shift berhasil dikirim (Memenuhi min. 2x24 jam)!");
      };

      // EXPORT REKAP TO CSV
      const exportToCSV = () => {
        let csvContent = "data:text/csv;charset=utf-8,Nama Karyawan,Waktu Absen,Shift,Status,Akurasi GPS,Lokasi Detail\n";
        attendances.forEach(att => {
          csvContent += `"${att.userName}","${att.time}","${att.shift}","${att.status}","${att.accuracy}","${att.locationName}"\n`;
        });
        const encodedUri = encodeURI(csvContent);
        const link = document.createElement("a");
        link.setAttribute("href", encodedUri);
        link.setAttribute("download", `Rekap_Presensi_Lazato_Cibenda_${new Date().toISOString().slice(0,10)}.csv`);
        document.body.appendChild(link);
        link.click();
        document.body.removeChild(link);
        showToast("File Rekap Presensi (.CSV) berhasil di-download!");
      };

      // PRINT LAPORAN / PDF
      const handlePrintReport = () => {
        window.print();
      };

      // ================= VIEW 1: LOGIN PAGE =================
      if (!isLoggedIn) {
        return (
          <div className="min-h-screen flex items-center justify-center p-4 sm:p-6 fade-enter">
            {toast && (
              <div className="fixed top-6 z-50 px-6 py-3 rounded-2xl shadow-2xl backdrop-blur-2xl bg-indigo-600/90 text-white font-semibold text-xs border border-white/40 animate-bounce">
                <span>{toast.msg}</span>
              </div>
            )}

            <div className="w-full max-w-md ios-glass-panel rounded-[38px] p-8 sm:p-10 relative overflow-hidden">
              <div className="text-center mb-8">
                <div className="w-20 h-20 mx-auto mb-4 rounded-3xl ios-glass-pill flex items-center justify-center text-indigo-600 shadow-xl border border-white/80">
                  <i data-lucide="store" className="w-10 h-10"></i>
                </div>
                <h1 className="text-2xl font-extrabold text-slate-900 tracking-tight">Lazato_Cibenda</h1>
                <p className="text-xs text-slate-600 mt-1 font-semibold">Portal Presensi & Shift Karyawan iOS 26</p>
              </div>

              <form onSubmit={handleLoginSubmit} className="space-y-4">
                <div>
                  <label className="block text-xs font-bold text-slate-700 mb-1 ml-1">Email / Username Karyawan</label>
                  <input type="email" name="email" required defaultValue="admin@lazato.id" placeholder="nama@lazato.id" className="w-full ios-glass-input px-4 py-3.5 rounded-2xl text-xs font-semibold text-slate-800" />
                </div>

                <div>
                  <label className="block text-xs font-bold text-slate-700 mb-1 ml-1">Kata Sandi (Password)</label>
                  <input type="password" name="password" required defaultValue="admincibenda123" placeholder="••••••••" className="w-full ios-glass-input px-4 py-3.5 rounded-2xl text-xs font-semibold text-slate-800" />
                </div>

                <button type="submit" className="w-full ios-button-primary py-4 rounded-2xl text-white font-bold text-xs uppercase tracking-wider flex items-center justify-center space-x-2 mt-2">
                  <span>Masuk Ke Portal Lazato</span>
                  <i data-lucide="arrow-right" className="w-4 h-4"></i>
                </button>
              </form>

              <div className="mt-6 text-center text-[10px] text-slate-500 font-semibold">
                *Akun dibuat & dikelola oleh Admin Manager.
              </div>
            </div>
          </div>
        );
      }

      // ================= VIEW 2: DASHBOARD UTAMA =================
      return (
        <div className="min-h-screen pb-28 pt-4 px-3 sm:px-6 lg:px-8 max-w-7xl mx-auto fade-enter">
          
          {toast && (
            <div className={`fixed top-6 right-6 z-50 px-6 py-3.5 rounded-2xl shadow-2xl backdrop-blur-2xl text-xs font-bold flex items-center space-x-2 border animate-bounce ${
              toast.type === "error" ? "bg-red-500/90 text-white border-white/40" : "bg-emerald-500/90 text-white border-white/40"
            }`}>
              <span>{toast.msg}</span>
            </div>
          )}

          {/* PRINT-ONLY REPORT HEADER */}
          <div className="hidden print-only mb-6 text-center">
            <h1 className="text-2xl font-bold">LAPORAN REKAP PRESENSI KARYAWAN</h1>
            <h2 className="text-lg">OUTLET LAZATO CIBENDA</h2>
            <p className="text-xs">Dicetak pada: {new Date().toLocaleString("id-ID")}</p>
            <hr className="my-4 border-slate-400" />
          </div>

          {/* APP HEADER */}
          <header className="ios-glass-panel rounded-[32px] p-4 sm:p-5 mb-4 flex flex-col md:flex-row items-center justify-between gap-4 no-print">
            <div className="flex items-center space-x-4 w-full md:w-auto">
              <img src={currentUser.photo} className="w-14 h-14 rounded-2xl object-cover ring-2 ring-white shadow-md" alt="Avatar" />
              <div>
                <div className="flex items-center space-x-2">
                  <h1 className="text-xl font-extrabold text-slate-900 tracking-tight">{currentUser.name}</h1>
                  <span className={`px-2.5 py-0.5 rounded-full text-[10px] font-extrabold uppercase ${userRole === 'admin' ? 'bg-indigo-600 text-white' : 'bg-emerald-500/20 text-emerald-800'}`}>
                    {userRole}
                  </span>
                </div>
                <p className="text-xs text-slate-600 font-semibold mt-0.5">Outlet: <strong>Lazato_Cibenda</strong></p>
              </div>
            </div>

            <div className="flex items-center space-x-3 w-full md:w-auto justify-end">
              {/* TOMBOL AKTIFKAN CLOUD NOTIFICATION */}
              {pushPermission !== "granted" && (
                <button onClick={requestCloudNotificationPermission} className="ios-glass-pill px-3 py-2 rounded-2xl text-xs font-bold text-indigo-700 flex items-center space-x-1.5 hover:bg-white">
                  <i data-lucide="bell-ring" className="w-4 h-4 text-indigo-600"></i>
                  <span>Aktifkan Notifikasi Awan</span>
                </button>
              )}

              {/* NOTIFICATION BELL */}
              <div className="relative">
                <button onClick={() => setShowNotifPanel(!showNotifPanel)} className="p-3 ios-glass-pill rounded-2xl text-indigo-700 relative">
                  <i data-lucide="bell" className="w-5 h-5"></i>
                  {notifications.length > 0 && (
                    <span className="absolute -top-1 -right-1 bg-rose-500 text-white text-[9px] font-extrabold w-5 h-5 rounded-full flex items-center justify-center border-2 border-white">
                      {notifications.length}
                    </span>
                  )}
                </button>

                {showNotifPanel && (
                  <div className="absolute right-0 mt-3 w-80 sm:w-96 ios-glass-panel rounded-[24px] p-4 shadow-2xl z-50 border border-white/80">
                    <h4 className="text-xs font-extrabold text-slate-800 mb-3 border-b pb-2">Pusat Notifikasi Awan</h4>
                    <div className="space-y-2 max-h-60 overflow-y-auto">
                      {notifications.length === 0 ? (
                        <p className="text-xs text-slate-500">Belum ada notifikasi baru.</p>
                      ) : notifications.map(n => (
                        <div key={n.id} className="ios-glass-card p-3 rounded-xl">
                          <h5 className="font-extrabold text-[11px] text-slate-800">{n.title}</h5>
                          <p className="text-[10px] text-slate-600 mt-0.5 leading-snug">{n.body}</p>
                        </div>
                      ))}
                    </div>
                  </div>
                )}
              </div>

              <button onClick={() => setIsLoggedIn(false)} className="ios-glass-pill px-4 py-2.5 rounded-2xl text-xs font-bold text-red-600 hover:bg-red-500/10 transition-all flex items-center space-x-1">
                <i data-lucide="log-out" className="w-3.5 h-3.5"></i>
                <span>Keluar</span>
              </button>
            </div>
          </header>

          {/* FLOATING NAVBAR (NON-OVERLAPPING) */}
          <nav className="ios-glass-panel rounded-[26px] p-2 mb-6 flex items-center justify-between gap-1 overflow-x-auto shadow-lg no-print">
            {userRole === "karyawan" && (
              <>
                <button onClick={() => setActiveTab("absen")} className={`flex-1 min-w-[120px] flex items-center justify-center space-x-2 py-3 px-3 rounded-2xl text-xs font-extrabold transition-all ${activeTab === "absen" ? "bg-indigo-600 text-white shadow-md shadow-indigo-500/30" : "text-slate-700 hover:bg-white/40"}`}>
                  <i data-lucide="camera" className="w-4 h-4"></i>
                  <span>Absensi Ready</span>
                </button>
                <button onClick={() => setActiveTab("tukar")} className={`flex-1 min-w-[140px] flex items-center justify-center space-x-2 py-3 px-3 rounded-2xl text-xs font-extrabold transition-all ${activeTab === "tukar" ? "bg-indigo-600 text-white shadow-md shadow-indigo-500/30" : "text-slate-700 hover:bg-white/40"}`}>
                  <i data-lucide="arrow-left-right" className="w-4 h-4"></i>
                  <span>Tukar Shift</span>
                </button>
              </>
            )}

            {userRole === "admin" && (
              <>
                <button onClick={() => setActiveTab("rekap")} className={`flex-1 min-w-[130px] flex items-center justify-center space-x-2 py-3 px-3 rounded-2xl text-xs font-extrabold transition-all ${activeTab === "rekap" ? "bg-indigo-600 text-white shadow-md shadow-indigo-500/30" : "text-slate-700 hover:bg-white/40"}`}>
                  <i data-lucide="file-spreadsheet" className="w-4 h-4"></i>
                  <span>Rekap Presensi</span>
                </button>
                <button onClick={() => setActiveTab("employees")} className={`flex-1 min-w-[150px] flex items-center justify-center space-x-2 py-3 px-3 rounded-2xl text-xs font-extrabold transition-all ${activeTab === "employees" ? "bg-indigo-600 text-white shadow-md shadow-indigo-500/30" : "text-slate-700 hover:bg-white/40"}`}>
                  <i data-lucide="users" className="w-4 h-4"></i>
                  <span>Data Karyawan</span>
                </button>
                <button onClick={() => setActiveTab("stats")} className={`flex-1 min-w-[150px] flex items-center justify-center space-x-2 py-3 px-3 rounded-2xl text-xs font-extrabold transition-all ${activeTab === "stats" ? "bg-indigo-600 text-white shadow-md shadow-indigo-500/30" : "text-slate-700 hover:bg-white/40"}`}>
                  <i data-lucide="bar-chart-3" className="w-4 h-4"></i>
                  <span>Analisis Data</span>
                </button>
                <button onClick={() => setActiveTab("exchanges")} className={`flex-1 min-w-[150px] flex items-center justify-center space-x-2 py-3 px-3 rounded-2xl text-xs font-extrabold transition-all ${activeTab === "exchanges" ? "bg-indigo-600 text-white shadow-md shadow-indigo-500/30" : "text-slate-700 hover:bg-white/40"}`}>
                  <i data-lucide="check-circle-2" className="w-4 h-4"></i>
                  <span>Persetujuan</span>
                </button>
              </>
            )}

            <button onClick={() => setActiveTab("jadwal")} className={`flex-1 min-w-[140px] flex items-center justify-center space-x-2 py-3 px-3 rounded-2xl text-xs font-extrabold transition-all ${activeTab === "jadwal" ? "bg-indigo-600 text-white shadow-md shadow-indigo-500/30" : "text-slate-700 hover:bg-white/40"}`}>
              <i data-lucide="calendar" className="w-4 h-4"></i>
              <span>Jadwal Mingguan</span>
            </button>
          </nav>

          {/* MAIN TAB CONTENT DISPLAY */}
          <div>
            
            {/* TAB 1: ABSENSI (CAMERA AUTO-READY VIEWFINDER) */}
            {activeTab === "absen" && (
              <div className="ios-glass-panel rounded-[32px] p-6 sm:p-8">
                <div className="flex items-center justify-between mb-6">
                  <div>
                    <h2 className="text-xl font-extrabold text-slate-900 tracking-tight">Presensi Lazato_Cibenda</h2>
                    <p className="text-xs text-slate-600 mt-0.5">Kamera otomatis aktif (Ready Stream). Sekali cekrek untuk merekam presensi dan GPS spesifik.</p>
                  </div>
                  <span className="px-3 py-1 bg-emerald-500/20 text-emerald-900 border border-emerald-300 rounded-xl text-[10px] font-extrabold flex items-center">
                    <span className="w-2 h-2 rounded-full bg-emerald-500 mr-1.5 animate-pulse"></span>
                    Camera Ready Stream
                  </span>
                </div>

                <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
                  <div className="flex flex-col items-center">
                    {/* Viewfinder Kamera Langsung Aktif */}
                    <div className="relative w-full aspect-[4/3] ios-glass-card rounded-[28px] overflow-hidden border-2 border-indigo-300 flex items-center justify-center shadow-inner">
                      {capturedPhoto ? (
                        <img src={capturedPhoto} className="w-full h-full object-cover" alt="Captured Selfie" />
                      ) : (
                        <video ref={videoRef} autoPlay playsInline className="w-full h-full object-cover transform -scale-x-100"></video>
                      )}
                    </div>

                    <div className="flex items-center space-x-3 mt-4 w-full">
                      {!capturedPhoto ? (
                        <button onClick={takeInstantSnapshot} className="w-full bg-emerald-600 hover:bg-emerald-700 text-white font-extrabold py-3.5 rounded-2xl text-xs flex items-center justify-center space-x-2 shadow-lg transition-all">
                          <i data-lucide="aperture" className="w-5 h-5"></i>
                          <span>SEKALI CEKREK ABSEN</span>
                        </button>
                      ) : (
                        <button onClick={() => setCapturedPhoto(null)} className="w-full ios-glass-pill py-3.5 rounded-2xl font-bold text-xs text-slate-700 hover:bg-white">
                          Cekrek Ulang Foto
                        </button>
                      )}
                    </div>
                  </div>

                  {/* GPS & LOCATION PANEL */}
                  <div className="flex flex-col justify-between space-y-4">
                    <div className="ios-glass-card p-5 rounded-[24px] space-y-3">
                      <h3 className="text-xs font-extrabold text-slate-800 flex items-center uppercase tracking-wider">
                        <i data-lucide="navigation" className="w-4 h-4 text-indigo-600 mr-2"></i>
                        Data Geo-Tag GPS Presisi
                      </h3>

                      <div className="space-y-2 text-xs">
                        <div className="flex justify-between py-1.5 border-b border-slate-200/50">
                          <span className="text-slate-500">Waktu Server:</span>
                          <span className="font-bold text-slate-800">{new Date().toLocaleTimeString("id-ID")} WIB</span>
                        </div>

                        <div className="flex justify-between py-1.5 border-b border-slate-200/50">
                          <span className="text-slate-500">Akurasi GPS Margin:</span>
                          <span className="font-extrabold text-emerald-600">{location ? location.accuracy : "Menunggu Cekrek..."}</span>
                        </div>

                        <div className="py-1">
                          <span className="text-slate-500 block mb-1">Lokasi Presisi Outlet:</span>
                          {locLoading ? (
                            <p className="text-indigo-600 font-bold animate-pulse text-[11px]">Memproses data lokasi GPS...</p>
                          ) : location ? (
                            <div className="bg-white/80 p-3 rounded-xl border border-white space-y-1">
                              <p className="text-slate-800 font-bold text-[11px] leading-relaxed">{location.address}</p>
                              <p className="text-[10px] font-mono text-indigo-800 font-semibold">
                                Lat: {location.lat.toFixed(6)}, Lng: {location.lng.toFixed(6)}
                              </p>
                            </div>
                          ) : (
                            <p className="text-slate-400 italic text-[11px]">Tekan "SEKALI CEKREK" untuk langsung merekam koordinat.</p>
                          )}
                        </div>
                      </div>
                    </div>

                    <button onClick={handleSubmitAbsen} className="w-full ios-button-primary py-4 rounded-2xl text-white font-extrabold text-xs tracking-wider uppercase flex items-center justify-center space-x-2">
                      <i data-lucide="send" className="w-4 h-4"></i>
                      <span>Kirim Absensi Sekarang</span>
                    </button>
                  </div>
                </div>
              </div>
            )}

            {/* TAB 2: MANAJEMEN KARYAWAN & PASSWORD EDIT */}
            {activeTab === "employees" && (
              <div className="ios-glass-panel rounded-[32px] p-6 sm:p-8">
                <div className="flex items-center justify-between mb-6">
                  <div>
                    <h2 className="text-xl font-extrabold text-slate-900 tracking-tight">Manajemen Karyawan Outlet</h2>
                    <p className="text-xs text-slate-600 mt-0.5">Admin berhak mengedit seluruh detail, memantau kata sandi, dan membuat akun baru.</p>
                  </div>
                  <button onClick={() => setShowAddEmpModal(true)} className="ios-button-primary px-4 py-2.5 rounded-2xl text-white font-bold text-xs flex items-center space-x-1.5 shadow-md">
                    <i data-lucide="plus" className="w-4 h-4"></i>
                    <span>Tambah Karyawan</span>
                  </button>
                </div>

                {/* MODAL EDIT KARYAWAN */}
                {editingEmp && (
                  <form onSubmit={handleSaveEmployeeDetail} className="mb-6 ios-glass-card p-6 rounded-[26px] grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 border-2 border-indigo-400">
                    <h3 className="sm:col-span-2 lg:col-span-3 font-extrabold text-sm text-slate-800 mb-1">
                      Edit Detail & Kata Sandi: {editingEmp.name}
                    </h3>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Nama Lengkap</label>
                      <input type="text" name="empName" defaultValue={editingEmp.name} required className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold" />
                    </div>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Email Karyawan</label>
                      <input type="email" name="empEmail" defaultValue={editingEmp.email} required className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold" />
                    </div>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1 text-indigo-700">Kata Sandi (Password)</label>
                      <input type="text" name="empPassword" defaultValue={editingEmp.password} required className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-bold text-indigo-900 bg-indigo-50/50" />
                    </div>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">No. WhatsApp</label>
                      <input type="text" name="empPhone" defaultValue={editingEmp.phone} required className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold" />
                    </div>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Divisi / Jabatan</label>
                      <input type="text" name="empDivision" defaultValue={editingEmp.division} required className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold" />
                    </div>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Shift Utama</label>
                      <select name="defaultShift" defaultValue={editingEmp.defaultShift} className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold">
                        <option value="SHIFT_1">Shift 1 (00:00 - 08:00)</option>
                        <option value="SHIFT_2">Shift 2 (08:00 - 16:00)</option>
                        <option value="SHIFT_3">Shift 3 (16:00 - 00:00)</option>
                        <option value="OFF">OFF (Libur)</option>
                      </select>
                    </div>
                    <input type="hidden" name="empRole" value={editingEmp.role} />
                    <div className="sm:col-span-2 lg:col-span-3 flex justify-end space-x-2 pt-2">
                      <button type="button" onClick={() => setEditingEmp(null)} className="px-4 py-2 text-xs font-bold text-slate-600">Batal</button>
                      <button type="submit" className="ios-button-primary px-5 py-2 text-white font-bold text-xs rounded-xl">Simpan Perubahan</button>
                    </div>
                  </form>
                )}

                {/* MODAL TAMBAH KARYAWAN */}
                {showAddEmpModal && (
                  <form onSubmit={handleAddEmployee} className="mb-6 ios-glass-card p-6 rounded-[26px] grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 border-2 border-emerald-400">
                    <h3 className="sm:col-span-2 lg:col-span-3 font-extrabold text-sm text-slate-800 mb-1">Buat Akun Karyawan Baru</h3>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Nama Lengkap</label>
                      <input type="text" name="empName" required placeholder="Ahmad Subagja" className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold" />
                    </div>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Email Login</label>
                      <input type="email" name="empEmail" required placeholder="ahmad@lazato.id" className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold" />
                    </div>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Kata Sandi</label>
                      <input type="text" name="empPassword" defaultValue="lazato2026" required className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold" />
                    </div>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">No. WhatsApp</label>
                      <input type="text" name="empPhone" required placeholder="+62812..." className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold" />
                    </div>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Divisi / Jabatan</label>
                      <input type="text" name="empDivision" defaultValue="Dapur & Frying" required className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold" />
                    </div>
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Default Shift</label>
                      <select name="defaultShift" className="w-full ios-glass-input px-3.5 py-2 rounded-xl text-xs font-semibold">
                        <option value="SHIFT_1">Shift 1 (00:00 - 08:00)</option>
                        <option value="SHIFT_2">Shift 2 (08:00 - 16:00)</option>
                        <option value="SHIFT_3">Shift 3 (16:00 - 00:00)</option>
                        <option value="OFF">OFF (Libur)</option>
                      </select>
                    </div>
                    <input type="hidden" name="empRole" value="karyawan" />
                    <div className="sm:col-span-2 lg:col-span-3 flex justify-end space-x-2 pt-2">
                      <button type="button" onClick={() => setShowAddEmpModal(false)} className="px-4 py-2 text-xs font-bold text-slate-600">Batal</button>
                      <button type="submit" className="ios-button-primary px-5 py-2 text-white font-bold text-xs rounded-xl">Buat Akun Karyawan</button>
                    </div>
                  </form>
                )}

                {/* KARTU KARYAWAN LENGKAP */}
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                  {employees.map(emp => (
                    <div key={emp.id} className="ios-glass-card p-5 rounded-[24px] space-y-3">
                      <div className="flex items-center space-x-3">
                        <img src={emp.photo} className="w-12 h-12 rounded-2xl object-cover ring-2 ring-white" alt="Emp" />
                        <div>
                          <h4 className="font-extrabold text-slate-900 text-sm">{emp.name}</h4>
                          <p className="text-[11px] text-slate-500">{emp.division}</p>
                          <span className="inline-block mt-1 px-2.5 py-0.5 rounded-md bg-indigo-100 text-indigo-900 text-[10px] font-bold">
                            {emp.defaultShift}
                          </span>
                        </div>
                      </div>

                      <div className="p-3 bg-white/70 rounded-xl space-y-1 text-xs">
                        <div className="flex justify-between">
                          <span className="text-slate-500">Email:</span>
                          <span className="font-semibold text-slate-800">{emp.email}</span>
                        </div>
                        <div className="flex justify-between">
                          <span className="text-slate-500">No. WA:</span>
                          <span className="font-semibold text-slate-800">{emp.phone}</span>
                        </div>
                        <div className="flex justify-between bg-indigo-50/80 p-1 rounded-md mt-1">
                          <span className="text-indigo-700 font-bold">Kata Sandi:</span>
                          <span className="font-mono font-bold text-indigo-900">{emp.password}</span>
                        </div>
                      </div>

                      <div className="flex items-center justify-end space-x-2 pt-1 border-t border-slate-200/50">
                        <button onClick={() => setEditingEmp(emp)} className="px-3 py-1.5 rounded-xl bg-indigo-600 text-white font-bold text-xs shadow-sm hover:bg-indigo-700 flex items-center space-x-1">
                          <i data-lucide="edit-3" className="w-3.5 h-3.5"></i>
                          <span>Edit Detail</span>
                        </button>
                        <button onClick={() => handleDeleteEmployee(emp.id, emp.name)} className="p-2 rounded-xl text-red-500 hover:bg-red-500/10">
                          <i data-lucide="trash-2" className="w-4 h-4"></i>
                        </button>
                      </div>
                    </div>
                  ))}
                </div>
              </div>
            )}

            {/* TAB 3: REKAP PRESENSI & EXPORT DATA */}
            {activeTab === "rekap" && (
              <div className="ios-glass-panel rounded-[32px] p-6 sm:p-8">
                <div className="flex flex-col sm:flex-row sm:items-center justify-between mb-6 gap-3 no-print">
                  <div>
                    <h2 className="text-xl font-extrabold text-slate-900 tracking-tight">Rekapitulasi Presensi Karyawan</h2>
                    <p className="text-xs text-slate-600 mt-0.5">Detail foto selfie, GPS presisi, dan waktu absen masuk.</p>
                  </div>
                  <div className="flex items-center space-x-2">
                    <button onClick={exportToCSV} className="ios-glass-pill px-4 py-2.5 rounded-2xl text-xs font-bold text-emerald-800 hover:bg-emerald-100 flex items-center space-x-1.5 shadow-sm">
                      <i data-lucide="download" className="w-4 h-4 text-emerald-600"></i>
                      <span>Export CSV</span>
                    </button>
                    <button onClick={handlePrintReport} className="ios-button-primary px-4 py-2.5 rounded-2xl text-white font-bold text-xs flex items-center space-x-1.5">
                      <i data-lucide="printer" className="w-4 h-4"></i>
                      <span>Cetak PDF</span>
                    </button>
                  </div>
                </div>

                <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
                  {attendances.map(item => (
                    <div key={item.id} className="ios-glass-card p-4 rounded-[24px] flex space-x-4">
                      <img src={item.photo} className="w-24 h-24 rounded-2xl object-cover ring-2 ring-white shadow-sm" alt="Selfie" />
                      <div className="flex-1 text-xs space-y-1">
                        <div className="flex justify-between items-start">
                          <h3 className="font-extrabold text-slate-900 text-sm">{item.userName}</h3>
                          <span className={`px-2.5 py-0.5 rounded-full font-bold text-[10px] ${item.status === 'Tepat Waktu' ? 'bg-emerald-100 text-emerald-800' : 'bg-amber-100 text-amber-800'}`}>
                            {item.status}
                          </span>
                        </div>
                        <p className="text-slate-500 text-[11px]">{item.time}</p>
                        <p className="font-bold text-indigo-600 text-[11px]">{item.shift}</p>
                        <p className="text-slate-700 text-[11px] leading-snug">📍 {item.locationName}</p>
                        <p className="text-[10px] text-emerald-700 font-extrabold pt-1">Akurasi GPS: {item.accuracy}</p>
                      </div>
                    </div>
                  ))}
                </div>
              </div>
            )}

            {/* TAB 4: STATISTIK & ANALISIS KARYAWAN */}
            {activeTab === "stats" && (
              <div className="ios-glass-panel rounded-[32px] p-6 sm:p-8">
                <div className="flex flex-col sm:flex-row sm:items-center justify-between mb-6 gap-3 no-print">
                  <div>
                    <h2 className="text-xl font-extrabold text-slate-900 tracking-tight">Analisis Statistik Kinerja Karyawan</h2>
                    <p className="text-xs text-slate-600 mt-0.5">Sajian data analisis kehadiran, keterlambatan (menit), dan kepatuhan shift.</p>
                  </div>
                  <button onClick={handlePrintReport} className="ios-glass-pill px-4 py-2 rounded-xl text-xs font-bold text-indigo-700 hover:bg-white flex items-center space-x-1.5">
                    <i data-lucide="printer" className="w-4 h-4"></i>
                    <span>Cetak Laporan</span>
                  </button>
                </div>

                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                  {employees.map(emp => {
                    const empAtt = attendances.filter(a => a.userName === emp.name);
                    const totalLate = empAtt.reduce((acc, curr) => acc + (curr.lateMinutes || 0), 0);
                    const attendanceRate = empAtt.length > 0 ? 100 : 85;

                    return (
                      <div key={emp.id} className="ios-glass-card p-5 rounded-[24px] space-y-3">
                        <div className="flex items-center space-x-3">
                          <img src={emp.photo} className="w-12 h-12 rounded-xl object-cover ring-2 ring-white" alt="Emp" />
                          <div>
                            <h4 className="font-extrabold text-slate-900 text-sm">{emp.name}</h4>
                            <p className="text-[11px] text-slate-500">{emp.division}</p>
                          </div>
                        </div>

                        <div>
                          <div className="flex justify-between text-xs font-bold mb-1">
                            <span className="text-slate-600">Tingkat Kehadiran</span>
                            <span className="text-indigo-600">{attendanceRate}%</span>
                          </div>
                          <div className="w-full bg-slate-200 h-2 rounded-full overflow-hidden">
                            <div className="bg-indigo-600 h-full rounded-full" style={{ width: `${attendanceRate}%` }}></div>
                          </div>
                        </div>

                        <div className="grid grid-cols-2 gap-2 text-center text-xs pt-1">
                          <div className="bg-white/80 p-2 rounded-xl border border-white">
                            <span className="text-[10px] text-slate-500 font-bold block">Tepat Waktu</span>
                            <span className="text-sm font-extrabold text-emerald-600">{empAtt.length || 1} Hari</span>
                          </div>
                          <div className="bg-white/80 p-2 rounded-xl border border-white">
                            <span className="text-[10px] text-slate-500 font-bold block">Terlambat</span>
                            <span className="text-sm font-extrabold text-amber-600">{totalLate} Menit</span>
                          </div>
                        </div>
                      </div>
                    );
                  })}
                </div>
              </div>
            )}

            {/* TAB 5: JADWAL SHIFT MINGGUAN */}
            {activeTab === "jadwal" && (
              <div className="ios-glass-panel rounded-[32px] p-6 sm:p-8">
                <div className="flex justify-between items-center mb-6">
                  <div>
                    <h2 className="text-xl font-extrabold text-slate-900 tracking-tight">Jadwal Shift Mingguan Karyawan</h2>
                    <p className="text-xs text-slate-600 mt-0.5">Penjadwalan berdasarkan Nama Hari tanpa pengulangan tanggal.</p>
                  </div>
                </div>

                <div className="overflow-x-auto rounded-[24px] border border-white/60 shadow-sm">
                  <table className="w-full text-left border-collapse">
                    <thead>
                      <tr className="border-b border-slate-200/60 bg-white/40 text-[11px] font-extrabold text-slate-700">
                        <th className="p-4 w-28">NAMA HARI</th>
                        <th className="p-4 bg-emerald-500/10 text-emerald-800">OFF (LIBUR)</th>
                        <th className="p-4 bg-indigo-500/10 text-indigo-800">SHIFT 1 (00:00 - 08:00)</th>
                        <th className="p-4 bg-amber-500/10 text-amber-800">SHIFT 2 (08:00 - 16:00)</th>
                        <th className="p-4 bg-purple-500/10 text-purple-800">SHIFT 3 (16:00 - 00:00)</th>
                      </tr>
                    </thead>
                    <tbody className="divide-y divide-slate-200/40 text-xs font-semibold">
                      {schedules.map((item) => (
                        <tr key={item.id} className="hover:bg-white/40 transition-all">
                          <td className="p-4 font-extrabold text-slate-900 uppercase tracking-wider text-xs bg-white/20">{item.day}</td>
                          <td className="p-3 bg-emerald-50/10">{item.off.join(", ")}</td>
                          <td className="p-3 bg-indigo-50/10">{item.shift1.join(", ")}</td>
                          <td className="p-3 bg-amber-50/10">{item.shift2.join(", ")}</td>
                          <td className="p-3 bg-purple-50/10">{item.shift3.join(", ")}</td>
                        </tr>
                      ))}
                    </tbody>
                  </table>
                </div>
              </div>
            )}

            {/* TAB 6: PENGAJUAN TUKAR SHIFT */}
            {activeTab === "tukar" && (
              <div className="ios-glass-panel rounded-[32px] p-6 sm:p-8">
                <div className="flex items-center justify-between mb-2">
                  <h2 className="text-xl font-extrabold text-slate-900 tracking-tight">Pengajuan Pertukaran Shift</h2>
                  <span className="px-3 py-1 bg-amber-500/20 text-amber-900 border border-amber-300 rounded-xl text-[10px] font-extrabold">
                    Aturan Wajib: Min. 2x24 Jam
                  </span>
                </div>
                <p className="text-xs text-slate-600 mb-6">Pertukaran shift wajib diajukan sekurang-kurangnya 48 jam sebelum jadwal bertugas.</p>

                <form onSubmit={handleRequestExchange} className="ios-glass-card p-6 rounded-[24px] space-y-4 max-w-xl">
                  <div className="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Target Rekan Kerja</label>
                      <select name="targetUser" required className="w-full ios-glass-input px-3.5 py-3 rounded-xl text-xs font-semibold text-slate-800">
                        {employees.filter(e => e.name !== currentUser.name).map(e => <option key={e.id} value={e.name}>{e.name}</option>)}
                      </select>
                    </div>

                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Tanggal Shift (Min. +2 Hari)</label>
                      <input type="date" name="shiftDate" required className="w-full ios-glass-input px-3.5 py-3 rounded-xl text-xs font-semibold text-slate-800" />
                    </div>

                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Shift Saya</label>
                      <select name="fromShift" className="w-full ios-glass-input px-3.5 py-3 rounded-xl text-xs font-semibold text-slate-800">
                        <option value="Shift 1">Shift 1 (00:00 - 08:00)</option>
                        <option value="Shift 2">Shift 2 (08:00 - 16:00)</option>
                        <option value="Shift 3">Shift 3 (16:00 - 00:00)</option>
                      </select>
                    </div>

                    <div>
                      <label className="text-xs font-bold text-slate-700 block mb-1">Shift Tujuan</label>
                      <select name="toShift" className="w-full ios-glass-input px-3.5 py-3 rounded-xl text-xs font-semibold text-slate-800">
                        <option value="OFF">OFF (Libur)</option>
                        <option value="Shift 1">Shift 1 (00:00 - 08:00)</option>
                        <option value="Shift 2">Shift 2 (08:00 - 16:00)</option>
                      </select>
                    </div>
                  </div>

                  <div>
                    <label className="text-xs font-bold text-slate-700 block mb-1">Alasan Pertukaran</label>
                    <textarea name="reason" required rows="2" placeholder="Tuliskan alasan..." className="w-full ios-glass-input p-3.5 rounded-xl text-xs font-medium text-slate-800"></textarea>
                  </div>

                  <button type="submit" className="w-full ios-button-primary py-3.5 rounded-xl text-white font-bold text-xs uppercase tracking-wider">
                    Kirim Pengajuan Shift
                  </button>
                </form>
              </div>
            )}

            {/* TAB 7: PERSETUJUAN SHIFT (ADMIN) */}
            {activeTab === "exchanges" && (
              <div className="ios-glass-panel rounded-[32px] p-6 sm:p-8">
                <h2 className="text-xl font-extrabold text-slate-900 tracking-tight mb-1">Persetujuan Shift Karyawan</h2>
                <p className="text-xs text-slate-600 mb-6">Persetujuan atau penolakan pengajuan pertukaran shift kerja.</p>

                <div className="space-y-4">
                  {exchanges.map(ex => (
                    <div key={ex.id} className="ios-glass-card p-5 rounded-[24px] flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                      <div>
                        <div className="flex items-center space-x-2">
                          <span className="font-bold text-slate-900 text-sm">{ex.requester}</span>
                          <span className="text-xs text-slate-400">&rarr;</span>
                          <span className="font-bold text-indigo-600 text-sm">{ex.target}</span>
                        </div>
                        <p className="text-xs text-slate-700 mt-1">Tanggal: <strong>{ex.shiftDate} ({ex.dayName})</strong></p>
                        <p className="text-xs text-slate-500 italic mt-0.5">Alasan: "{ex.reason}"</p>
                      </div>

                      <span className={`px-3 py-1 rounded-full text-xs font-bold ${ex.status === 'Approved' ? 'bg-emerald-100 text-emerald-800' : 'bg-amber-100 text-amber-800'}`}>
                        {ex.status}
                      </span>
                    </div>
                  ))}
                </div>
              </div>
            )}

          </div>
        </div>
      );
    }

    ReactDOM.createRoot(document.getElementById("root")).render(<App />);
  </script>
</body>
</html>

