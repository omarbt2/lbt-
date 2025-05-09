<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>المواد الدراسية - ثانوية الصديق بن يحيى</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    body {
      font-family: 'Cairo', sans-serif;
      background-color: #f5f7fa;
    }
    .selection-card {
      transition: all 0.3s ease;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
    }
    .selection-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1);
    }
    .subject-badge {
      font-size: 0.85rem;
      padding: 0.35rem 0.7rem;
    }
    .nav-link:hover {
      color: #3b82f6;
      transform: translateX(-3px);
    }
    .exam-card {
      transition: all 0.2s ease;
      cursor: pointer;
    }
    .exam-card:hover {
      transform: translateY(-2px);
      box-shadow: 0 5px 10px rgba(0, 0, 0, 0.1);
    }
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }
    .modal-content {
      background-color: white;
      width: 90%;
      max-width: 600px;
      border-radius: 10px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
      animation: modalFadeIn 0.3s ease;
    }
    @keyframes modalFadeIn {
      from { opacity: 0; transform: translateY(-20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .modal-header {
      padding: 15px 20px;
      border-bottom: 1px solid #eee;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .modal-body {
      padding: 20px;
      max-height: 70vh;
      overflow-y: auto;
    }
    .modal-footer {
      padding: 15px 20px;
      border-top: 1px solid #eee;
      text-align: left;
    }
    .close-modal {
      background: none;
      border: none;
      font-size: 1.5rem;
      cursor: pointer;
      color: #777;
    }
    .exam-preview {
      width: 100%;
      height: 300px;
      border: 1px solid #ddd;
      margin-bottom: 15px;
      background: #f9f9f9;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #666;
    }
    .loading-spinner {
      display: none;
      width: 2rem;
      height: 2rem;
      border: 0.25rem solid rgba(59, 130, 246, 0.2);
      border-top-color: #3b82f6;
      border-radius: 50%;
      animation: spin 1s linear infinite;
    }
    @keyframes spin {
      100% { transform: rotate(360deg); }
    }
    /* إضافة بسيطة لكلمة Beta */
    .beta-text {
      display: inline-block;
      background-color: #f59e0b;
      color: white;
      font-size: 0.75rem;
      padding: 2px 8px;
      border-radius: 12px;
      margin-right: 5px;
      vertical-align: super;
    }
  </style>
</head>
<body class="text-gray-800 bg-gradient-to-b from-blue-50 to-gray-50">
  <!-- Header -->
  <header class="bg-gradient-to-r from-blue-600 to-blue-800 text-white shadow-lg">
    <div class="container mx-auto px-4 py-3 flex flex-col md:flex-row justify-between items-center">
      <div class="flex items-center mb-4 md:mb-0">
        <img src="https://via.placeholder.com/50" alt="شعار الثانوية" class="ml-3 h-12 w-12 object-contain">
        <div>
          <h1 class="text-xl md:text-2xl font-bold">ثانوية محمد الصديق بن يحيى <span class="beta-text">Beta</span></h1>
          <p class="text-sm text-blue-100">بلدية القليعة - ولاية تيبازة</p>
        </div>
      </div>
      
      <nav class="flex flex-wrap justify-center gap-2 md:gap-4">
        <a href="index.html" class="nav-link px-3 py-1 rounded-lg hover:bg-blue-500 transition flex items-center">
          <i class="fas fa-home ml-2"></i> الرئيسية
        </a>
        <a href="subjects.html" class="nav-link px-3 py-1 rounded-lg bg-blue-500 hover:bg-blue-600 transition flex items-center">
          <i class="fas fa-book-open ml-2"></i> المواد
        </a>
        <a href="library.html" class="nav-link px-3 py-1 rounded-lg hover:bg-blue-500 transition flex items-center">
          <i class="fas fa-book ml-2"></i> المكتبة
        </a>
        <a href="timetable.html" class="nav-link px-3 py-1 rounded-lg hover:bg-blue-500 transition flex items-center">
          <i class="fas fa-calendar-alt ml-2"></i> الجدول
        </a>
        <a href="login.html" class="nav-link px-3 py-1 rounded-lg bg-yellow-500 hover:bg-yellow-600 transition flex items-center">
          <i class="fas fa-sign-in-alt ml-2"></i> دخول
        </a>
      </nav>
    </div>
  </header>

  <!-- بقية الكود كما هو تماما -->
  <!-- Main Content -->
  <main class="container mx-auto py-8 px-4">
    <div class="text-center mb-10">
      <h2 class="text-3xl font-bold text-blue-700 mb-2">المواد الدراسية</h2>
      <p class="text-gray-600 max-w-2xl mx-auto">اختر السنة والشعبة والمادة لعرض الاختبارات المتاحة</p>
    </div>

    <div class="bg-white rounded-xl shadow-md overflow-hidden max-w-4xl mx-auto">
      <!-- Selection Steps -->
      <div class="p-6 md:p-8">
        <!-- Year Selection -->
        <div class="mb-8">
          <h3 class="text-xl font-semibold text-gray-800 mb-4 flex items-center">
            <span class="bg-blue-100 text-blue-800 rounded-full w-8 h-8 flex items-center justify-center mr-3">1</span>
            اختر السنة الدراسية
          </h3>
          <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
            <button data-year="1as" class="year-btn selection-card bg-white border border-blue-200 rounded-lg p-4 text-center hover:border-blue-400">
              <i class="fas fa-star text-yellow-400 text-2xl mb-2"></i>
              <h4 class="font-bold text-lg">السنة الأولى</h4>
              <p class="text-sm text-gray-600 mt-1">جذع مشترك علوم</p>
            </button>
            <button data-year="2as" class="year-btn selection-card bg-white border border-blue-200 rounded-lg p-4 text-center hover:border-blue-400">
              <i class="fas fa-star-half-alt text-orange-400 text-2xl mb-2"></i>
              <h4 class="font-bold text-lg">السنة الثانية</h4>
              <p class="text-sm text-gray-600 mt-1">شعب متنوعة</p>
            </button>
            <button data-year="3as" class="year-btn selection-card bg-white border border-blue-200 rounded-lg p-4 text-center hover:border-blue-400">
              <i class="fas fa-graduation-cap text-blue-400 text-2xl mb-2"></i>
              <h4 class="font-bold text-lg">السنة الثالثة</h4>
              <p class="text-sm text-gray-600 mt-1">تحضير البكالوريا</p>
            </button>
          </div>
        </div>
        
        <!-- Stream Selection -->
        <div class="mb-8 hidden" id="stream-section">
          <h3 class="text-xl font-semibold text-gray-800 mb-4 flex items-center">
            <span class="bg-blue-100 text-blue-800 rounded-full w-8 h-8 flex items-center justify-center mr-3">2</span>
            اختر الشعبة
          </h3>
          <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4" id="stream-container">
            <!-- Stream buttons will be added here by JavaScript -->
          </div>
        </div>
        
        <!-- Subject Selection -->
        <div class="hidden" id="subject-section">
          <h3 class="text-xl font-semibold text-gray-800 mb-4 flex items-center">
            <span class="bg-blue-100 text-blue-800 rounded-full w-8 h-8 flex items-center justify-center mr-3">3</span>
            اختر المادة الدراسية
          </h3>
          <div class="flex flex-wrap gap-3" id="subject-container">
            <!-- Subject buttons will be added here by JavaScript -->
          </div>
        </div>
      </div>
      
      <!-- Exams Section -->
      <div class="bg-gray-50 border-t border-gray-200 p-6 hidden" id="exams-section">
        <div class="flex justify-between items-center mb-6">
          <h3 class="text-xl font-semibold text-gray-800 flex items-center">
            <i class="fas fa-file-pdf text-blue-500 ml-2"></i>
            اختبارات مادة: <span id="selected-subject" class="text-blue-600 mx-2"></span>
            <span class="text-gray-600">للشعبة: <span id="selected-stream" class="font-medium"></span></span>
          </h3>
          <div id="loading-spinner" class="loading-spinner"></div>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4" id="exams-container">
          <!-- Exams will be loaded here -->
        </div>
        
        <div id="no-exams-message" class="hidden text-center py-8">
          <i class="fas fa-folder-open text-gray-400 text-4xl mb-4"></i>
          <h4 class="text-lg font-medium text-gray-600">لا توجد اختبارات متاحة حالياً</h4>
          <p class="text-gray-500 mt-2">يمكنك المحاولة لاحقاً أو اختيار مادة أخرى</p>
        </div>
      </div>
    </div>
  </main>

  <!-- Footer -->
  <footer class="bg-gray-800 text-white py-8 mt-12">
    <div class="container mx-auto px-4">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
        <div>
          <h3 class="text-lg font-bold mb-4">ثانوية الصديق بن يحيى</h3>
          <p class="text-gray-400">منصة تعليمية متكاملة لطلاب التعليم الثانوي في الجزائر</p>
        </div>
        <div>
          <h3 class="text-lg font-bold mb-4">روابط سريعة</h3>
          <ul class="space-y-2">
            <li><a href="index.html" class="text-gray-400 hover:text-white transition">الرئيسية</a></li>
            <li><a href="https://tharwa.education.gov.dz" target="_blank" class="text-gray-400 hover:text-white transition">المكتبة الرقمية</a></li>
            <li><a href="timetable.html" class="text-gray-400 hover:text-white transition">الجدول الدراسي</a></li>
            <li><a href="https://tharwa.education.gov.dz" target="_blank" class="text-gray-400 hover:text-white transition">النتائج المدرسية</a></li>
          </ul>
        </div>
        <div>
          <h3 class="text-lg font-bold mb-4">تواصل معنا</h3>
          <ul class="space-y-2">
            <li class="flex items-center text-gray-400">
              <i class="fas fa-phone-alt ml-2"></i> 024482240
            </li>
            <li class="flex items-center text-gray-400">
              <i class="fas fa-envelope ml-2"></i> contact@lycee-dz.edu
            </li>
            <li class="flex items-center text-gray-400">
              <i class="fas fa-map-marker-alt ml-2"></i> القليعة، تيبازة
            </li>
          </ul>
        </div>
        <div>
          <h3 class="text-lg font-bold mb-4">تابعنا</h3>
          <div class="flex space-x-4 space-x-reverse">
            <a href="https://www.facebook.com/Nounoukolea" target="_blank" class="bg-gray-700 hover:bg-blue-600 w-10 h-10 rounded-full flex items-center justify-center transition">
              <i class="fab fa-facebook-f"></i>
            </a>
            <a href="#" class="bg-gray-700 hover:bg-blue-400 w-10 h-10 rounded-full flex items-center justify-center transition">
              <i class="fab fa-twitter"></i>
            </a>
            <a href="https://www.instagram.com/prof_noureddine/" target="_blank" class="bg-gray-700 hover:bg-pink-600 w-10 h-10 rounded-full flex items-center justify-center transition">
              <i class="fab fa-instagram"></i>
            </a>
            <a href="#" class="bg-gray-700 hover:bg-red-600 w-10 h-10 rounded-full flex items-center justify-center transition">
              <i class="fab fa-youtube"></i>
            </a>
          </div>
        </div>
      </div>
      <div class="border-t border-gray-700 mt-8 pt-6 text-center text-gray-400">
        <p>© 2030 جميع الحقوق محفوظة - ثانوية محمد الصديق بن يحيى</p>
      </div>
    </div>
  </footer>

  <!-- Modal -->
  <div id="examModal" class="modal">
    <div class="modal-content">
      <div class="modal-header">
        <h3 id="modalExamTitle" class="text-lg font-bold text-gray-800"></h3>
        <button class="close-modal">&times;</button>
      </div>
      <div class="modal-body">
        <div class="exam-preview">
          <p>معاينة للاختبار تظهر هنا</p>
        </div>
        <div class="mb-4">
          <h4 class="font-bold text-gray-700 mb-2">معلومات الاختبار:</h4>
          <p id="modalExamDescription" class="text-gray-600"></p>
          <div class="flex flex-wrap gap-2 mt-3">
            <span id="modalExamType" class="bg-blue-100 text-blue-800 px-3 py-1 rounded-full text-sm"></span>
            <span id="modalExamDate" class="bg-gray-100 text-gray-800 px-3 py-1 rounded-full text-sm"></span>
            <span id="modalExamYear" class="bg-green-100 text-green-800 px-3 py-1 rounded-full text-sm"></span>
          </div>
        </div>
        <div class="mb-4">
          <h4 class="font-bold text-gray-700 mb-2">تعليمات:</h4>
          <ul class="list-disc pr-5 text-gray-600 space-y-1">
            <li>زمن الاختبار: 60 دقيقة</li>
            <li>عدد الأسئلة: 20 سؤال</li>
            <li>الدرجة الكلية: 20 نقطة</li>
          </ul>
        </div>
      </div>
      <div class="modal-footer">
        <a id="modalDownloadLink" href="#" target="_blank" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-lg inline-flex items-center">
          <i class="fas fa-download ml-2"></i> تحميل الاختبار
        </a>
        <button id="modalPrintLink" class="bg-gray-200 hover:bg-gray-300 text-gray-800 px-4 py-2 rounded-lg mr-2 inline-flex items-center">
          <i class="fas fa-print ml-2"></i> طباعة
        </button>
      </div>
    </div>
  </div>

  <script>
    // البيانات الهيكلية للمواد حسب السنوات والشعب
    const educationalData = {
      "1as": {
        name: "السنة الأولى ثانوي",
        streams: {
          "جذع علوم وتكنولوجيا": {
            subjects: [
              "الرياضيات", "العلوم الطبيعية", "العلوم الفيزيائية", 
              "اللغة العربية", "اللغة الفرنسية", "اللغة الإنجليزية",
              "التاريخ والجغرافيا", "الفلسفة", "التربية الإسلامية",
              "التربية المدنية", "الإعلام الآلي"
            ],
            icon: "flask"
          },
          "جذع آداب": {
            subjects: [
              "اللغة العربية", "اللغة الفرنسية", "اللغة الإنجليزية", 
              "الرياضيات", "العلوم الطبيعية", "العلوم الفيزيائية",
              "التاريخ والجغرافيا", "الفلسفة", "التربية الإسلامية",
              "التربية المدنية", "الإعلام الآلي"
            ],
            icon: "book-open"
          }
        }
      },
      "2as": {
        name: "السنة الثانية ثانوي",
        streams: {
          "علوم تجريبية": {
            subjects: [
              "الرياضيات", "العلوم الطبيعية", "العلوم الفيزيائية",
              "اللغة العربية", "اللغة الفرنسية", "اللغة الإنجليزية",
              "الفلسفة", "التاريخ والجغرافيا", "التربية الإسلامية"
            ],
            icon: "microscope"
          },
          "رياضيات": {
            subjects: [
              "الرياضيات", "العلوم الفيزيائية", "العلوم الطبيعية",
              "اللغة العربية", "اللغة الفرنسية", "اللغة الإنجليزية",
              "الفلسفة", "التاريخ والجغرافيا", "التربية الإسلامية"
            ],
            icon: "square-root-alt"
          },
          "تقني رياضي": {
            subjects: [
              "الرياضيات", "العلوم الفيزيائية", "التكنولوجيا",
              "اللغة العربية", "اللغة الفرنسية", "اللغة الإنجليزية",
              "الفلسفة", "التاريخ والجغرافيا", "التربية الإسلامية"
            ],
            icon: "robot"
          },
          "تسيير واقتصاد": {
            subjects: [
              "الرياضيات", "علوم التسيير والاقتصاد", "القانون",
              "الاقتصاد والمحاسبة", "اللغة العربية", "اللغة الفرنسية",
              "اللغة الإنجليزية", "الفلسفة", "التاريخ والجغرافيا",
              "التربية الإسلامية"
            ],
            icon: "chart-line"
          },
          "آداب وفلسفة": {
            subjects: [
              "اللغة العربية", "الفلسفة", "التاريخ والجغرافيا",
              "اللغة الفرنسية", "اللغة الإنجليزية", "الرياضيات",
              "التربية الإسلامية"
            ],
            icon: "pen-fancy"
          },
          "لغات أجنبية": {
            subjects: [
              "اللغة العربية", "اللغة الفرنسية", "اللغة الإنجليزية",
              "اللغة الأجنبية الثالثة", "الفلسفة", "التاريخ والجغرافيا",
              "الرياضيات", "التربية الإسلامية"
            ],
            icon: "language"
          }
        }
      },
      "3as": {
        name: "السنة الثالثة ثانوي",
        streams: {
          "علوم تجريبية": {
            subjects: [
              "الرياضيات", "العلوم الطبيعية", "العلوم الفيزيائية",
              "اللغة العربية", "اللغة الفرنسية", "اللغة الإنجليزية",
              "الفلسفة", "التاريخ والجغرافيا", "التربية الإسلامية"
            ],
            icon: "microscope"
          },
          "رياضيات": {
            subjects: [
              "الرياضيات", "العلوم الفيزيائية", "العلوم الطبيعية",
              "اللغة العربية", "اللغة الفرنسية", "اللغة الإنجليزية",
              "الفلسفة", "التاريخ والجغرافيا", "التربية الإسلامية"
            ],
            icon: "square-root-alt"
          },
          "تقني رياضي": {
            subjects: [
              "الرياضيات", "العلوم الفيزيائية", "التكنولوجيا",
              "اللغة العربية", "اللغة الفرنسية", "اللغة الإنجليزية",
              "الفلسفة", "التاريخ والجغرافيا", "التربية الإسلامية"
            ],
            icon: "robot"
          },
          "تسيير واقتصاد": {
            subjects: [
              "الرياضيات", "علوم التسيير والاقتصاد", "القانون",
              "الاقتصاد والمحاسبة", "اللغة العربية", "اللغة الفرنسية",
              "اللغة الإنجليزية", "الفلسفة", "التاريخ والجغرافيا",
              "التربية الإسلامية"
            ],
            icon: "chart-line"
          },
          "آداب وفلسفة": {
            subjects: [
              "اللغة العربية", "الفلسفة", "التاريخ والجغرافيا",
              "اللغة الفرنسية", "اللغة الإنجليزية", "الرياضيات",
              "التربية الإسلامية"
            ],
            icon: "pen-fancy"
          },
          "لغات أجنبية": {
            subjects: [
              "اللغة العربية", "اللغة الفرنسية", "اللغة الإنجليزية",
              "اللغة الأجنبية الثالثة", "الفلسفة", "التاريخ والجغرافيا",
              "الرياضيات", "التربية الإسلامية"
            ],
            icon: "language"
          }
        }
      }
    };

    // روابط المواد من موقع dzexams.com
    const subjectUrls = {
      "الرياضيات": {
        exams: "mathematiques/examens"
      },
      "العلوم الفيزيائية": {
        exams: "physique/examens"
      },
      "اللغة العربية": {
        exams: "arabe/examens"
      },
      "اللغة الفرنسية": {
        exams: "francais/examens"
      },
      "اللغة الإنجليزية": {
        exams: "anglais/examens"
      },
      "التاريخ والجغرافيا": {
        exams: "histoire-geographie/examens"
      },
      "العلوم الطبيعية": {
        exams: "sciences-naturelles/examens"
      },
      "الفلسفة": {
        exams: "philosophie/examens"
      },
      "التربية الإسلامية": {
        exams: "education-islamique/examens"
      },
      "التربية المدنية": {
        exams: "education-civique/examens"
      },
      "الإعلام الآلي": {
        exams: "informatique/examens"
      }
    };

    // متغيرات لتخزين الاختيارات
    let selectedYear = null;
    let selectedStream = null;
    let selectedSubject = null;

    // عناصر واجهة المستخدم
    const yearButtons = document.querySelectorAll('.year-btn');
    const streamSection = document.getElementById('stream-section');
    const streamContainer = document.getElementById('stream-container');
    const subjectSection = document.getElementById('subject-section');
    const subjectContainer = document.getElementById('subject-container');
    const examsSection = document.getElementById('exams-section');
    const examsContainer = document.getElementById('exams-container');
    const noExamsMessage = document.getElementById('no-exams-message');
    const selectedSubjectSpan = document.getElementById('selected-subject');
    const selectedStreamSpan = document.getElementById('selected-stream');
    const loadingSpinner = document.getElementById('loading-spinner');

    // عناصر النافذة المنبثقة
    const examModal = document.getElementById('examModal');
    const modalExamTitle = document.getElementById('modalExamTitle');
    const modalExamDescription = document.getElementById('modalExamDescription');
    const modalExamType = document.getElementById('modalExamType');
    const modalExamDate = document.getElementById('modalExamDate');
    const modalExamYear = document.getElementById('modalExamYear');
    const modalDownloadLink = document.getElementById('modalDownloadLink');
    const modalPrintLink = document.getElementById('modalPrintLink');
    const closeModalBtn = document.querySelector('.close-modal');

    // معالجة اختيار السنة
    yearButtons.forEach(button => {
      button.addEventListener('click', function() {
        // إزالة التنشيط من جميع الأزرار
        yearButtons.forEach(btn => {
          btn.classList.remove('border-blue-500', 'bg-blue-50');
          btn.classList.add('border-blue-200');
        });
        
        // تنشيط الزر المحدد
        this.classList.remove('border-blue-200');
        this.classList.add('border-blue-500', 'bg-blue-50');
        
        // تعيين السنة المختارة
        selectedYear = this.dataset.year;
        
        // عرض قسم الشعبة
        streamSection.classList.remove('hidden');
        
        // إخفاء الأقسام اللاحقة
        subjectSection.classList.add('hidden');
        examsSection.classList.add('hidden');
        
        // تحميل الشعب المتاحة لهذه السنة
        loadStreams(selectedYear);
      });
    });

    // تحميل الشعب المتاحة للسنة المحددة
    function loadStreams(year) {
      streamContainer.innerHTML = '';
      
      const streams = educationalData[year].streams;
      
      for (const [streamName, streamData] of Object.entries(streams)) {
        const streamButton = document.createElement('button');
        streamButton.className = 'stream-btn selection-card bg-white border border-blue-200 rounded-lg p-4 text-center hover:border-blue-400 flex flex-col items-center';
        streamButton.dataset.stream = streamName;
        
        streamButton.innerHTML = `
          <i class="fas fa-${streamData.icon} text-blue-400 text-2xl mb-2"></i>
          <h4 class="font-bold text-lg">${streamName}</h4>
          <p class="text-sm text-gray-600 mt-1">${streamData.subjects.length} مادة</p>
        `;
        
        streamButton.addEventListener('click', function() {
          // إزالة التنشيط من جميع أزرار الشعب
          document.querySelectorAll('.stream-btn').forEach(btn => {
            btn.classList.remove('border-blue-500', 'bg-blue-50');
            btn.classList.add('border-blue-200');
          });
          
          // تنشيط الزر المحدد
          this.classList.remove('border-blue-200');
          this.classList.add('border-blue-500', 'bg-blue-50');
          
          // تعيين الشعبة المختارة
          selectedStream = this.dataset.stream;
          
          // عرض قسم المواد
          subjectSection.classList.remove('hidden');
          
          // إخفاء قسم الاختبارات
          examsSection.classList.add('hidden');
          
          // تحميل المواد المتاحة لهذه الشعبة
          loadSubjects(year, selectedStream);
        });
        
        streamContainer.appendChild(streamButton);
      }
    }

    // تحميل المواد المتاحة للشعبة المحددة
    function loadSubjects(year, stream) {
      subjectContainer.innerHTML = '';
      
      const subjects = educationalData[year].streams[stream].subjects;
      
      subjects.forEach(subject => {
        const subjectButton = document.createElement('button');
        subjectButton.className = 'subject-btn bg-white hover:bg-blue-50 border border-gray-200 rounded-full px-4 py-2 text-sm font-medium transition flex items-center';
        subjectButton.textContent = subject;
        
        subjectButton.addEventListener('click', function() {
          // إزالة التنشيط من جميع أزرار المواد
          document.querySelectorAll('.subject-btn').forEach(btn => {
            btn.classList.remove('bg-blue-100', 'border-blue-300', 'text-blue-800');
            btn.classList.add('border-gray-200');
          });
          
          // تنشيط الزر المحدد
          this.classList.remove('border-gray-200');
          this.classList.add('bg-blue-100', 'border-blue-300', 'text-blue-800');
          
          // تعيين المادة المختارة
          selectedSubject = subject;
          
          // عرض الاختبارات
          loadExams(year, stream, subject);
        });
        
        subjectContainer.appendChild(subjectButton);
      });
    }

    // تحميل الاختبارات للمادة المختارة
    async function loadExams(year, stream, subject) {
      // عرض رسالة التحميل
      examsContainer.innerHTML = '';
      noExamsMessage.classList.add('hidden');
      loadingSpinner.style.display = 'block';
      examsSection.classList.remove('hidden');
      
      // تعيين المعلومات المختارة
      selectedSubjectSpan.textContent = subject;
      selectedStreamSpan.textContent = stream;
      
      try {
        // جلب الاختبارات من dzexams.com
        const exams = await fetchExamsFromDzExams(year, subject);
        
        // إخفاء رسالة التحميل
        loadingSpinner.style.display = 'none';
        
        if (exams.length > 0) {
          // عرض الاختبارات
          examsContainer.innerHTML = '';
          exams.forEach(exam => {
            const examCard = document.createElement('div');
            examCard.className = 'exam-card bg-white rounded-lg shadow p-4 border border-gray-200 hover:border-blue-300 flex items-start';
            
            examCard.innerHTML = `
              <div class="bg-blue-100 p-3 rounded-lg mr-4">
                <i class="fas fa-file-pdf text-blue-600"></i>
              </div>
              <div class="flex-1">
                <h4 class="font-bold text-gray-800">${exam.title}</h4>
                <p class="text-sm text-gray-600 mt-1">${exam.description}</p>
                <div class="flex items-center mt-3 text-xs text-gray-500">
                  <span class="bg-gray-100 px-2 py-1 rounded mr-2">${exam.type}</span>
                  <span>${exam.date}</span>
                </div>
              </div>
              <div class="text-blue-500 ml-2">
                <i class="fas fa-chevron-left"></i>
              </div>
            `;
            
            examCard.addEventListener('click', () => openExamModal(exam));
            examsContainer.appendChild(examCard);
          });
        } else {
          // لا توجد اختبارات
          noExamsMessage.classList.remove('hidden');
        }
      } catch (error) {
        console.error('Error loading exams:', error);
        loadingSpinner.style.display = 'none';
        noExamsMessage.classList.remove('hidden');
      }
    }

    // فتح النافذة المنبثقة لعرض تفاصيل الاختبار
    function openExamModal(exam) {
      modalExamTitle.textContent = exam.title;
      modalExamDescription.textContent = exam.description;
      modalExamType.textContent = exam.type;
      modalExamDate.textContent = exam.date;
      modalExamYear.textContent = exam.year || selectedYear.replace('as', '') + ' ثانوي';
      modalDownloadLink.href = exam.url;
      
      examModal.style.display = 'flex';
      document.body.style.overflow = 'hidden';
    }

    // إغلاق النافذة المنبثقة
    function closeExamModal() {
      examModal.style.display = 'none';
      document.body.style.overflow = 'auto';
    }

    // أحداث النافذة المنبثقة
    closeModalBtn.addEventListener('click', closeExamModal);
    examModal.addEventListener('click', function(e) {
      if (e.target === examModal) {
        closeExamModal();
      }
    });

    // زر الطباعة
    modalPrintLink.addEventListener('click', function() {
      window.print();
    });

    // محاكاة جلب الاختبارات من dzexams.com
    async function fetchExamsFromDzExams(year, subject) {
      // في التطبيق الفعلي، هنا ستقوم بجلب البيانات الحقيقية من الموقع
      // هذه مجرد محاكاة للبيانات للتوضيح
      return new Promise(resolve => {
        setTimeout(() => {
          if (subjectUrls[subject]) {
            const baseUrl = `https://www.dzexams.com/ar/${year}/${subjectUrls[subject].exams}`;
            
            resolve([
              {
                title: "اختبار الفصل الأول",
                description: "اختبار نموذجي لمادة " + subject + " يتضمن أسئلة متنوعة تغطي كافة جوانب المقرر",
                type: "فصل أول",
                date: "ديسمبر 2022",
                year: year.replace('as', '') + ' ثانوي',
                url: baseUrl + "/examen1"
              },
              {
                title: "اختبار الفصل الثاني",
                description: "اختبار شامل لمادة " + subject + " مع حلول نموذجية",
                type: "فصل ثاني",
                date: "مارس 2023",
                year: year.replace('as', '') + ' ثانوي',
                url: baseUrl + "/examen2"
              },
              {
                title: "اختبار تجريبي",
                description: "اختبار تحضيري لمادة " + subject + " مع تصحيح ذاتي",
                type: "تجريبي",
                date: "مايو 2023",
                year: year.replace('as', '') + ' ثانوي',
                url: baseUrl + "/examen3"
              }
            ]);
          } else {
            resolve([]);
          }
        }, 1000); // محاكاة زمن التحميل
      });
    }

    // إضافة تأثيرات عند التمرير
    window.addEventListener('scroll', function() {
      const header = document.querySelector('header');
      if (window.scrollY > 50) {
        header.classList.add('shadow-lg');
      } else {
        header.classList.remove('shadow-lg');
      }
    });

    // تهيئة الصفحة عند التحميل
    document.addEventListener('DOMContentLoaded', function() {
      // يمكنك هنا إضافة أي تهيئة إضافية تحتاجها
    });
  </script>
</body>
</html>
