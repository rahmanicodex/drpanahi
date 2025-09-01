<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
  <!-- شِبه-Blade: @extends('layouts.app')  -->
  <!-- شِبه-Blade: @section('title', 'دکتر پناهی | جراح عمومی') -->
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <meta name="csrf-token" content="eyJmYWtlX2xhcmF2ZWxfY3NyZiI6InhZQ0ZqT1h2S0pEN2pyaG0ifQ==" />
  <title>دکتر پناهی | جراح عمومی</title>
  <meta name="description" content="وب‌سایت شخصی دکتر پناهی، جراح عمومی. نوبت‌گیری آنلاین، معرفی خدمات جراحی، مقالات آموزشی و راه‌های ارتباط." />

  <!-- شبیه asset() و mix(): در پروژه لاراول معمولا فایل‌ها با query نسخه می‌آیند -->
  <!-- <link rel="stylesheet" href="/assets/app.css?id=fe32a1" /> -->

  <style>
    :root{
      --bg: #0b0f14;
      --card: #101824;
      --card-2: #0f141c;
      --text: #e7edf5;
      --muted: #a7b1c2;
      --brand: #6bd3ff;
      --brand-2: #8ef3c1;
      --danger: #ff6b86;
      --warning: #ffcf6b;
      --ok: #7df18a;
      --ring: rgba(107, 211, 255, .35);
      --shadow: 0 20px 45px rgba(0,0,0,.35);
      --radius-2xl: 1.25rem;
      --radius-xl: 1rem;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0; font-family: system-ui, -apple-system, Segoe UI, Roboto, "Vazirmatn", "IRANSans", sans-serif;
      background: radial-gradient(1200px 800px at 80% -10%, rgba(107,211,255,.15), transparent 60%),
                  radial-gradient(900px 600px at 10% 110%, rgba(142,243,193,.16), transparent 60%),
                  var(--bg);
      color:var(--text); line-height:1.75; overflow-x:hidden;
    }
    a{color:inherit; text-decoration:none}
    .container{width:min(1120px, 92vw); margin-inline:auto}

    /* ناوبری */
    .nav{
      position:sticky; top:0; z-index:50; backdrop-filter:saturate(160%) blur(12px);
      background:linear-gradient(180deg, rgba(16,24,36,.85), rgba(16,24,36,.55));
      border-bottom:1px solid rgba(255,255,255,.06);
    }
    .nav .row{display:flex; align-items:center; justify-content:space-between; padding:14px 0}
    .brand{display:flex; align-items:center; gap:10px; font-weight:800; letter-spacing:.2px}
    .brand .logo{display:grid; place-items:center; width:38px; height:38px; border-radius:14px; background:
      radial-gradient(120% 120% at 20% 15%, #6bd3ff, transparent 55%),
      radial-gradient(100% 100% at 85% 65%, #8ef3c1, transparent 55%), var(--card);
      box-shadow: inset 0 0 0 1px rgba(255,255,255,.06), 0 8px 24px rgba(0,0,0,.35);
    }
    .nav-links{display:flex; gap:18px; align-items:center}
    .nav a.link{padding:8px 12px; border-radius:12px; color:var(--muted); border:1px solid transparent}
    .nav a.link.active, .nav a.link:hover{color:var(--text); border-color:rgba(255,255,255,.07); background:rgba(255,255,255,.03)}
    .btn{
      display:inline-flex; align-items:center; gap:8px; padding:10px 14px; border-radius:14px;
      background:linear-gradient(180deg, #6bd3ff, #63a4ff); color:#012; font-weight:700; border:0;
      box-shadow:0 12px 24px rgba(99,164,255,.3); cursor:pointer
    }
    .btn.ghost{background:transparent; border:1px solid rgba(255,255,255,.1); color:var(--text); box-shadow:none}

    /* هیرو */
    .hero{padding:64px 0 28px; position:relative}
    .hero-grid{display:grid; grid-template-columns: 1.3fr 1fr; gap:28px}
    .badge{display:inline-flex; align-items:center; gap:8px; padding:6px 10px; border-radius:999px;
      color:#062; background:rgba(142,243,193,.18); border:1px solid rgba(142,243,193,.35)}
    .headline{font-size:clamp(28px, 4vw, 44px); line-height:1.25; margin:12px 0 14px; font-weight:900}
    .lead{color:var(--muted); font-size:18px}
    .kpis{display:grid; grid-template-columns: repeat(3, 1fr); gap:16px; margin-top:22px}
    .kpis .card{background:linear-gradient(180deg, rgba(255,255,255,.04), rgba(255,255,255,.02)); border:1px solid rgba(255,255,255,.07);
      border-radius:var(--radius-2xl); padding:16px 18px; box-shadow:var(--shadow)}
    .kpis .metric{font-size:28px; font-weight:900}
    .doctor-card{background:linear-gradient(180deg, rgba(107,211,255,.18), rgba(107,211,255,.06));
      border:1px solid rgba(107,211,255,.35); border-radius:28px; box-shadow:var(--shadow); padding:18px; position:relative}
    .doctor-card img{width:100%; border-radius:22px; display:block}
    .ribbon{position:absolute; top:18px; left:18px; background:#0b1520; border:1px solid rgba(255,255,255,.1); color:var(--brand);
      padding:6px 12px; border-radius:999px; font-weight:800; box-shadow:0 12px 24px rgba(0,0,0,.45)}

    /* کارت‌ها و سکشن‌ها */
    section{padding:32px 0}
    .section-title{display:flex; align-items:center; justify-content:space-between; margin-bottom:14px}
    .section-title h2{font-size:22px; margin:0}
    .cards{display:grid; grid-template-columns: repeat(3, 1fr); gap:18px}
    .card{background:var(--card); border:1px solid rgba(255,255,255,.06); border-radius:var(--radius-2xl); padding:18px; box-shadow:var(--shadow)}
    .card:hover{transform:translateY(-3px); transition:.2s ease}
    .chip{display:inline-flex; align-items:center; gap:8px; padding:6px 10px; border-radius:999px; border:1px solid rgba(255,255,255,.08); color:var(--muted)}

    /* جدول زمانی */
    .timeline{display:grid; gap:12px}
    .timeline .row{display:grid; grid-template-columns: 150px 1fr; gap:12px; align-items:start}
    .timeline .row .when{color:var(--muted)}
    .timeline .row .what{background:var(--card-2); padding:14px; border-radius:16px; border:1px solid rgba(255,255,255,.06)}

    /* فرم نوبت */
    .form{display:grid; gap:12px}
    .grid-2{display:grid; grid-template-columns:1fr 1fr; gap:12px}
    .input, .select, .textarea{
      width:100%; background:rgba(255,255,255,.03); border:1px solid rgba(255,255,255,.09);
      color:var(--text); border-radius:14px; padding:12px; outline:none;
    }
    .input:focus, .select:focus, .textarea:focus{box-shadow:0 0 0 4px var(--ring); border-color:rgba(107,211,255,.45)}
    .help{color:var(--muted); font-size:.9rem}
    .errors{display:none; background:rgba(255,107,134,.12); border:1px solid rgba(255,107,134,.35); color:#ffdbe3; padding:10px; border-radius:12px}

    /* کارت مقاله به سبک کارت‌های لاراول با فلش پیام */
    .flash{display:none; position:fixed; bottom:18px; right:18px; padding:12px 16px; border-radius:14px; background:linear-gradient(180deg, #8ef3c1, #4de3a6); color:#012; font-weight:800; box-shadow:var(--shadow); z-index:60}

    /* فوتر */
    footer{padding:24px 0 42px; color:var(--muted)}
    .footer-grid{display:grid; grid-template-columns: 2fr 1fr 1fr; gap:18px}
    .sep{border-top:1px dashed rgba(255,255,255,.08); margin:22px 0}

    /* ریسپانسیو */
    @media (max-width: 980px){
      .hero-grid{grid-template-columns:1fr}
      .cards{grid-template-columns:1fr 1fr}
      .footer-grid{grid-template-columns:1fr 1fr}
    }
    @media (max-width: 640px){
      .nav .row{padding:10px 0}
      .cards{grid-template-columns:1fr}
      .kpis{grid-template-columns:1fr 1fr}
      .timeline .row{grid-template-columns:1fr}
      .grid-2{grid-template-columns:1fr}
    }

    /* اسکلِتون برای لود مقالات (حس حرفه‌ای) */
    .skeleton{position:relative; overflow:hidden; background:rgba(255,255,255,.06); border-radius:14px; height:120px}
    .skeleton::after{content:""; position:absolute; inset:0; background:linear-gradient(90deg, transparent, rgba(255,255,255,.08), transparent); transform:translateX(-100%); animation:shimmer 1.6s infinite}
    @keyframes shimmer{to{transform:translateX(100%)}}

    /* Breadcrumbs شِبه-لاراول */
    .breadcrumbs{display:flex; gap:8px; align-items:center; color:var(--muted); font-size:.95rem}
    .breadcrumbs a{color:var(--muted)}
    .breadcrumbs svg{opacity:.65}
  </style>
</head>
<body>
  <!-- شِبه-Blade: @section('content') -->
  <header class="nav">
    <div class="container row">
      <a class="brand" href="/">
        <span class="logo" aria-hidden>
          <!-- لوگو ساده با SVG -->
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M12 3l8 4.5v9L12 21l-8-4.5v-9L12 3z" stroke="white" opacity=".55"/>
            <path d="M12 6l5.5 3.1v5.8L12 18l-5.5-3.1V9.1L12 6z" fill="url(#g)"/>
            <defs>
              <linearGradient id="g" x1="0" y1="0" x2="1" y2="1">
                <stop stop-color="#6bd3ff"/>
                <stop offset="1" stop-color="#8ef3c1"/>
              </linearGradient>
            </defs>
          </svg>
        </span>
        <span>کلینیک جراحی دکتر پناهی</span>
      </a>
      <nav class="nav-links">
        <!-- حس Route های لاراول /about /services /appointments /blog -->
        <a class="link active" href="#home">خانه</a>
        <a class="link" href="#services">خدمات</a>
        <a class="link" href="#appointments">نوبت‌گیری</a>
        <a class="link" href="#blog">مقالات</a>
        <a class="link" href="#contact">تماس</a>
        <button class="btn ghost" id="darkToggle" aria-label="تغییر حالت">حالت تیره/روشن</button>
      </nav>
    </div>
  </header>

  <main class="container">
    <section id="home" class="hero">
      <div class="breadcrumbs" aria-label="breadcrumbs">
        <!-- شِبه-Blade: {{ Breadcrumbs::render('home') }} -->
        <a href="/">خانه</a>
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none"><path d="M9 6l6 6-6 6" stroke="currentColor"/></svg>
        <span>معرفی</span>
      </div>
      <div class="hero-grid">
        <div>
          <span class="badge">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none"><circle cx="12" cy="12" r="10" stroke="#8ef3c1"/><path d="M7 12l3 3 7-7" stroke="#8ef3c1"/></svg>
            جراح عمومی | تخصص لاپاراسکوپی
          </span>
          <h1 class="headline">دکتر پناهی؛ دقت جراحی، آرامش بیمار</h1>
          <p class="lead">سال‌ها تجربه در جراحی‌های عمومی و کم‌تهاجمی، با تمرکز بر نتیجه‌ی ایمن و بهبود سریع بیمار. نوبت‌گیری سریع، مشاوره آنلاین و پیگیری درمان.</p>
          <div style="display:flex; gap:10px; margin-top:14px">
            <a class="btn" href="#appointments">نوبت‌گیری آنلاین</a>
            <a class="btn ghost" href="#services">مشاهده خدمات</a>
          </div>
          <div class="kpis">
            <div class="card"><div class="metric">+۱۲ سال</div><div class="help">تجربه‌ی جراحی</div></div>
            <div class="card"><div class="metric">۹۸٪</div><div class="help">رضایت بیماران</div></div>
            <div class="card"><div class="metric">+۳۰۰۰</div><div class="help">عمل موفق</div></div>
          </div>
        </div>
        <aside class="doctor-card">
          <span class="ribbon">کلینیک معتبر</span>
          <!-- در پروژه واقعی: <img src="{{ asset('storage/doctor-panahi.jpg') }}" alt="Dr Panahi"/> -->
          <img src="https://images.unsplash.com/photo-1622253692010-333f2da603d3?q=80&w=1200&auto=format&fit=crop" alt="دکتر پناهی"/>
          <div style="display:flex; gap:8px; margin-top:12px">
            <span class="chip">شماره نظام پزشکی: ۱۲۳۴۵۶</span>
            <span class="chip">تهران، خیابان ولیعصر</span>
          </div>
        </aside>
      </div>
    </section>

    <section id="services">
      <div class="section-title">
        <h2>خدمات جراحی</h2>
        <div class="chip">حسِ ماژولار لاراول: <code>resources/views/services/index.blade.php</code></div>
      </div>
      <div class="cards">
        <article class="card">
          <h3>لاپاراسکوپی کیسه صفرا</h3>
          <p class="help">برش‌های کوچک، درد کمتر، بهبود سریع‌تر.</p>
        </article>
        <article class="card">
          <h3>جراحی فتق</h3>
          <p class="help">شبکه تقویتی، بازگشت به فعالیت در کوتاه‌ترین زمان.</p>
        </article>
        <article class="card">
          <h3>تیرویید و پاراتیرویید</h3>
          <p class="help">رویکرد محافظه‌کارانه با هدایت سونوگرافی.</p>
        </article>
        <article class="card">
          <h3>جراحی هموروئید (فیشر/فیستول)</h3>
          <p class="help">تکنیک‌های کم‌تهاجمی و مراقبت پس از عمل.</p>
        </article>
        <article class="card">
          <h3>بیوپسی و اکسزیون توده‌های نرم</h3>
          <p class="help">تشخیص سریع و مدیریت زخم پیشرفته.</p>
        </article>
        <article class="card">
          <h3>مشاوره قبل عمل</h3>
          <p class="help">پرسش‌های رایج، داروها و آمادگی روز عمل.</p>
        </article>
      </div>
    </section>

    <section id="experience">
      <div class="section-title">
        <h2>سوابق و افتخارات</h2>
        <span class="chip">Route: <code>/about</code></span>
      </div>
      <div class="timeline">
        <div class="row"><div class="when">۱۳۹۴–۱۴۰۰</div><div class="what">جراح عمومی – بیمارستان XYZ تهران</div></div>
        <div class="row"><div class="when">۱۴۰۰–اکنون</div><div class="what">سرپرست تیم لاپاراسکوپی – کلینیک پیشرفته آلفا</div></div>
        <div class="row"><div class="when">جوایز</div><div class="what">برگزیده کنفرانس جراحی کم‌تهاجمی ۱۴۰۱</div></div>
      </div>
    </section>

    <section id="appointments">
      <div class="section-title">
        <h2>نوبت‌گیری آنلاین</h2>
        <span class="chip">Controller: <code>AppointmentsController@store</code></span>
      </div>
      <form class="card form" id="apptForm" novalidate>
        <!-- شِبه-Blade: @csrf -->
        <input type="hidden" name="_token" value="" id="csrfInput" />
        <div class="grid-2">
          <div>
            <label>نام و نام‌خانوادگی</label>
            <input class="input" type="text" name="name" placeholder="مثلا: سارا رضایی" required />
          </div>
          <div>
            <label>شماره تماس</label>
            <input class="input" type="tel" name="phone" placeholder="09xxxxxxxxx" required pattern="^0\d{10}$" />
          </div>
        </div>
        <div class="grid-2">
          <div>
            <label>نوع خدمت</label>
            <select class="select" name="service" required>
              <option value="">انتخاب کنید…</option>
              <option>لاپاراسکوپی کیسه صفرا</option>
              <option>جراحی فتق</option>
              <option>تیرویید</option>
              <option>هموروئید</option>
              <option>مشاوره پیش‌عمل</option>
            </select>
          </div>
          <div>
            <label>تاریخ پیشنهادی</label>
            <input class="input" type="date" name="date" required />
          </div>
        </div>
        <div>
          <label>توضیحات</label>
          <textarea class="textarea" name="notes" rows="3" placeholder="علائم، شرایط خاص، داروها…"></textarea>
        </div>
        <div class="errors" id="formErrors"></div>
        <div style="display:flex; gap:10px; align-items:center">
          <button class="btn" type="submit">ثبت نوبت</button>
          <span class="help">ارسال امن با توکن CSRF (نمایشی)</span>
        </div>
      </form>
    </section>

    <section id="blog">
      <div class="section-title">
        <h2>مقالات آموزشی</h2>
        <span class="chip">Route: <code>/blog</code></span>
      </div>
      <div class="cards" id="blogCards">
        <div class="card skeleton" aria-hidden="true"></div>
        <div class="card skeleton" aria-hidden="true"></div>
        <div class="card skeleton" aria-hidden="true"></div>
      </div>
    </section>

    <section id="contact">
      <div class="section-title">
        <h2>راه‌های ارتباط</h2>
        <span class="chip">Mail: <code>support@dr-panahi.ir</code></span>
      </div>
      <div class="cards">
        <div class="card">
          <h3>آدرس کلینیک</h3>
          <p class="help">تهران، ولیعصر، خیابان X، پلاک ۱۲ | ساعت کاری: ۹–۱۹</p>
          <a class="btn ghost" href="#">نمایش روی نقشه</a>
        </div>
        <div class="card">
          <h3>شبکه‌های اجتماعی</h3>
          <p class="help">اینستاگرام، ایتا، واتساپ</p>
          <div style="display:flex; gap:8px">
            <a class="chip" href="#">Instagram</a>
            <a class="chip" href="#">WhatsApp</a>
            <a class="chip" href="#">Telegram</a>
          </div>
        </div>
        <div class="card">
          <h3>پاسخ‌گویی سریع</h3>
          <p class="help">سوال فوری دارید؟ فرم تماس را پر کنید تا با شما تماس بگیریم.</p>
          <a class="btn" href="#appointments">ثبت پیام</a>
        </div>
      </div>
    </section>

    <div class="sep"></div>

    <footer class="container">
      <div class="footer-grid">
        <div>
          <strong>کلینیک جراحی دکتر پناهی</strong>
          <p class="help">با تکیه بر تجربه، تکنولوژی و تیم حرفه‌ای در کنار شما هستیم.</p>
        </div>
        <div>
          <strong>مسیرهای سریع</strong>
          <nav style="display:grid; gap:6px; margin-top:6px">
            <a href="#services">خدمات</a>
            <a href="#appointments">نوبت‌گیری</a>
            <a href="#blog">مقالات</a>
            <a href="#contact">تماس</a>
          </nav>
        </div>
        <div>
          <strong>خبرنامه</strong>
          <form id="newsletter" style="display:flex; gap:8px; margin-top:6px">
            <input class="input" type="email" placeholder="ایمیل شما" required />
            <button class="btn" type="submit">عضویت</button>
          </form>
          <small class="help">لغو عضویت هر زمان ممکن است.</small>
        </div>
      </div>
      <div class="sep"></div>
      <div style="display:flex; align-items:center; justify-content:space-between">
        <small class="help">© <span id="year"></span> همه حقوق محفوظ است.</small>
        <small class="help">ساخته‌شده به سبک لاراول (Front-end Static)</small>
      </div>
    </footer>
  </main>

  <div class="flash" id="flash"></div>

  <script>
    // شِبه-Blade: @push('scripts') ... @endpush
    // Dark/Light Toggle با ذخیره در localStorage
    const darkToggle = document.getElementById('darkToggle');
    darkToggle.addEventListener('click', () => {
      const current = document.documentElement.dataset.theme || 'dark';
      const next = current === 'dark' ? 'light' : 'dark';
      document.documentElement.dataset.theme = next;
      localStorage.setItem('theme', next);
      document.body.style.background = next === 'dark'
        ? `radial-gradient(1200px 800px at 80% -10%, rgba(107,211,255,.15), transparent 60%),
           radial-gradient(900px 600px at 10% 110%, rgba(142,243,193,.16), transparent 60%),
           var(--bg)`
        : '#f6f9fc';
      document.body.style.color = next === 'dark' ? 'var(--text)' : '#0b0f14';
    });
    const savedTheme = localStorage.getItem('theme');
    if(savedTheme){
      document.documentElement.dataset.theme = savedTheme;
      if(savedTheme === 'light') { document.body.style.background='#f6f9fc'; document.body.style.color='#0b0f14'; }
    }

    // شبیه csrf لاراول
    const meta = document.querySelector('meta[name="csrf-token"]').content;
    document.getElementById('csrfInput').value = meta;

    // فرم نوبت با ولیدیشن به سبک errors لاراول
    const apptForm = document.getElementById('apptForm');
    const errorsBox = document.getElementById('formErrors');
    const flash = document.getElementById('flash');

    apptForm.addEventListener('submit', async (e) => {
      e.preventDefault();
      errorsBox.style.display = 'none';
      errorsBox.innerHTML = '';

      const data = Object.fromEntries(new FormData(apptForm).entries());
      const errs = [];
      if(!data.name || data.name.trim().length < 3) errs.push('نام معتبر وارد کنید.');
      if(!/^0\d{10}$/.test(data.phone||'')) errs.push('شماره تماس معتبر نیست.');
      if(!data.service) errs.push('نوع خدمت را انتخاب کنید.');
      if(!data.date) errs.push('تاریخ را انتخاب کنید.');

      if(errs.length){
        errorsBox.style.display = 'block';
        errorsBox.innerHTML = '<ul style="margin:0; padding-right:18px">'+errs.map(e=>`<li>• ${e}</li>`).join('')+'</ul>';
        return;
      }

      // حسِ درخواست به /api/appointments با هدر X-CSRF-TOKEN
      try{
        await new Promise(r=>setTimeout(r, 900)); // شبیه درخواست شبکه
        // پاسخ موفق
        apptForm.reset();
        showFlash('نوبت شما با موفقیت ثبت شد. همکاران ما هماهنگ می‌کنند.');
      }catch(err){
        errorsBox.style.display = 'block';
        errorsBox.textContent = 'خطا در ثبت نوبت. بعدا تلاش کنید.';
      }
    });

    function showFlash(msg){
      flash.textContent = msg;
      flash.style.display = 'inline-flex';
      flash.style.opacity = '0';
      flash.style.transform = 'translateY(10px)';
      requestAnimationFrame(()=>{
        flash.style.transition = 'all .3s ease';
        flash.style.opacity = '1';
        flash.style.transform = 'translateY(0)';
      });
      setTimeout(()=>{
        flash.style.opacity = '0';
        flash.style.transform = 'translateY(10px)';
        setTimeout(()=> flash.style.display='none', 300);
      }, 2600);
    }

    // شبیه دریافت مقالات از Route: /api/posts
    const blogCards = document.getElementById('blogCards');
    setTimeout(()=>{
      const posts = [
        {title:'هرآنچه باید درباره لاپاراسکوپی بدانید', excerpt:'مزایا، عوارض احتمالی و آمادگی‌های پیش از عمل.'},
        {title:'راهنمای مراقبت پس از جراحی فتق', excerpt:'تغذیه، تحرک و علائمی که باید جدی بگیریم.'},
        {title:'تیرویید؛ چه زمانی نیاز به جراحی است؟', excerpt:'ارزیابی بالینی و پاراکلینیک پیش از تصمیم نهایی.'}
      ];
      blogCards.innerHTML = posts.map(p=>`
        <article class="card">
          <h3>${p.title}</h3>
          <p class="help">${p.excerpt}</p>
          <a class="btn ghost" href="#">ادامه مطلب</a>
        </article>
      `).join('');
    }, 1100);

    // سال فوتر
    document.getElementById('year').textContent = new Date().getFullYear();

    // هایلایت لینک فعال هنگام اسکرول (حس حرفه‌ای)
    const links = document.querySelectorAll('.nav a.link');
    const sections = [...document.querySelectorAll('main section')];
    const obs = new IntersectionObserver((entries)=>{
      entries.forEach(ent=>{
        if(ent.isIntersecting){
          links.forEach(a=>a.classList.remove('active'));
          const id = '#'+ent.target.id;
          const l = [...links].find(a=>a.getAttribute('href')===id);
          if(l) l.classList.add('active');
        }
      })
    }, {rootMargin:'-35% 0px -60% 0px', threshold:.1});
    sections.forEach(s=>obs.observe(s));
  </script>
  <!-- شِبه-Blade: @endsection -->
</body>
</html>
