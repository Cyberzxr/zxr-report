<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>گزارش تخلفات - @hadafmohakeme2</title>
    <style>
        /* همون استایل قبلی */
        * { margin:0; padding:0; box-sizing:border-box; }
        body {
            background: linear-gradient(135deg, #0a0a0f, #1a0a0a, #0d0d1a);
            font-family: 'Segoe UI', Tahoma, Arial, sans-serif;
            color: #fff;
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            max-width: 950px;
            margin: 0 auto;
            background: rgba(20,10,15,0.92);
            border-radius: 24px;
            padding: 40px;
            border: 1px solid rgba(255,50,50,0.25);
            box-shadow: 0 0 80px rgba(255,0,0,0.08);
        }
        .header { text-align:center; border-bottom:2px solid rgba(255,50,50,0.2); padding-bottom:30px; margin-bottom:30px; }
        .badge { display:inline-block; background:#ff1a1a; color:#fff; padding:6px 20px; border-radius:50px; font-size:13px; font-weight:700; letter-spacing:1px; text-transform:uppercase; margin-bottom:15px; }
        .header h1 { font-size:32px; background:linear-gradient(135deg,#ff4444,#ff8800); -webkit-background-clip:text; -webkit-text-fill-color:transparent; font-weight:900; }
        .header .sub { color:#999; font-size:16px; margin-top:8px; }
        .stats { display:grid; grid-template-columns:repeat(auto-fit,minmax(140px,1fr)); gap:15px; margin-bottom:35px; }
        .stat-card { background:rgba(255,255,255,0.04); border-radius:14px; padding:18px; text-align:center; border:1px solid rgba(255,255,255,0.06); }
        .stat-card .num { font-size:32px; font-weight:900; color:#ff4444; }
        .stat-card .label { font-size:13px; color:#888; margin-top:4px; }
        .violation-list { margin:25px 0; max-height:300px; overflow-y:auto; }
        .violation-item { background:rgba(255,50,50,0.06); border-right:3px solid #ff3333; padding:10px 14px; margin-bottom:6px; border-radius:0 10px 10px 0; font-size:13px; transition:all 0.2s; }
        .violation-item:hover { background:rgba(255,50,50,0.12); }
        .violation-item a { color:#ff6666; text-decoration:none; word-break:break-all; }
        .violation-item a:hover { color:#ffaa66; text-decoration:underline; }
        .section-title { font-size:20px; font-weight:700; color:#ff6666; margin:30px 0 15px 0; display:flex; align-items:center; gap:10px; }
        .section-title span { font-size:24px; }
        .email-box { background:rgba(255,255,255,0.04); border-radius:16px; padding:25px; margin-top:30px; border:1px solid rgba(255,255,255,0.08); }
        .email-box textarea { width:100%; height:200px; background:rgba(0,0,0,0.4); border:1px solid rgba(255,255,255,0.1); border-radius:12px; color:#ddd; padding:15px; font-size:13px; font-family:'Segoe UI',Tahoma,Arial,sans-serif; resize:vertical; direction:rtl; }
        .email-box textarea:focus { outline:none; border-color:#ff4444; }
        .btn-group { display:flex; gap:12px; flex-wrap:wrap; margin-top:18px; }
        .btn { padding:14px 28px; border:none; border-radius:50px; font-size:15px; font-weight:700; cursor:pointer; transition:all 0.3s; text-decoration:none; display:inline-flex; align-items:center; gap:8px; }
        .btn-primary { background:linear-gradient(135deg,#ff1a1a,#cc0000); color:#fff; box-shadow:0 4px 25px rgba(255,0,0,0.3); }
        .btn-primary:hover { transform:translateY(-2px); box-shadow:0 8px 40px rgba(255,0,0,0.5); }
        .btn-secondary { background:rgba(255,255,255,0.08); color:#ccc; border:1px solid rgba(255,255,255,0.1); }
        .btn-secondary:hover { background:rgba(255,255,255,0.15); }
        .btn-success { background:linear-gradient(135deg,#00cc66,#00994d); color:#fff; box-shadow:0 4px 25px rgba(0,204,102,0.25); }
        .btn-success:hover { transform:translateY(-2px); box-shadow:0 8px 40px rgba(0,204,102,0.4); }
        .btn-gold { background:linear-gradient(135deg,#f7971e,#ffd200); color:#000; box-shadow:0 4px 25px rgba(255,210,0,0.25); }
        .btn-gold:hover { transform:translateY(-2px); box-shadow:0 8px 40px rgba(255,210,0,0.4); }
        .footer { text-align:center; color:#555; font-size:13px; margin-top:35px; padding-top:20px; border-top:1px solid rgba(255,255,255,0.05); }
        .toast { position:fixed; bottom:30px; right:30px; background:#00cc66; color:#fff; padding:14px 28px; border-radius:12px; font-weight:600; opacity:0; transform:translateY(30px); transition:all 0.4s; pointer-events:none; box-shadow:0 8px 40px rgba(0,204,102,0.3); z-index:999; }
        .toast.show { opacity:1; transform:translateY(0); }
        @media (max-width:600px) { .container { padding:20px; } .header h1 { font-size:24px; } .stat-card .num { font-size:24px; } .btn { padding:12px 18px; font-size:13px; width:100%; justify-content:center; } .btn-group { flex-direction:column; } }
        .email-grid { display:grid; grid-template-columns:1fr 1fr; gap:8px; margin-top:10px; }
        .email-chip { background:rgba(255,255,255,0.06); padding:8px 14px; border-radius:8px; text-align:center; font-size:12px; color:#aaa; border:1px solid rgba(255,255,255,0.05); }
        .email-chip strong { color:#ff6666; }
        .counter-box { background:rgba(255,50,50,0.08); border-radius:14px; padding:15px 20px; margin:15px 0; text-align:center; border:1px solid rgba(255,50,50,0.15); }
        .counter-box .big { font-size:48px; font-weight:900; color:#ff4444; }
        .counter-box .desc { color:#888; font-size:14px; margin-top:4px; }
    </style>
</head>
<body>

<div class="container">
    
    <div class="header">
        <div class="badge">🚨 ۹۲ تخلف شناسایی شد</div>
        <h1>گزارش تخلفات چنل</h1>
        <div class="sub">@hadafmohakeme2 · انتشار اطلاعات شخصی · نقض حریم خصوصی</div>
    </div>
    
    <div class="stats">
        <div class="stat-card"><div class="num">۹۲</div><div class="label">تخلفات</div></div>
        <div class="stat-card"><div class="num">۱۰۰%</div><div class="label">اطلاعات شخصی</div></div>
        <div class="stat-card"><div class="num">⛔</div><div class="label">نقض حریم خصوصی</div></div>
        <div class="stat-card"><div class="num">🔥</div><div class="label">نیاز به برخورد فوری</div></div>
    </div>
    
    <div class="counter-box">
        <div class="big">۱۰۰</div>
        <div class="desc">نفر در حال ارسال گزارش هستند · با هم می‌تونیم این چنل رو ببندیم 💪</div>
    </div>
    
    <div class="section-title"><span>📋</span> لیست کامل لینک‌های تخلف (۹۲ مورد)</div>
    <div class="violation-list" id="violationList"></div>
    
    <div class="section-title"><span>✉️</span> گزارش به تمام ایمیل‌های تلگرام</div>
    
    <div class="email-grid">
        <div class="email-chip"><strong>abuse@telegram.org</strong> · اصلی</div>
        <div class="email-chip"><strong>dmca@telegram.org</strong> · حق نشر</div>
        <div class="email-chip"><strong>support@telegram.org</strong> · پشتیبانی</div>
        <div class="email-chip"><strong>security@telegram.org</strong> · امنیت</div>
        <div class="email-chip"><strong>privacy@telegram.org</strong> · حریم خصوصی</div>
        <div class="email-chip"><strong>press@telegram.org</strong> · رسانه</div>
    </div>
    
    <div class="email-box">
        <textarea id="emailBody" readonly>گزارش تخلفات چنل @hadafmohakeme2

🔴 انتشار اطلاعات شخصی در 92 مورد

لینک‌های تخلف:
https://t.me/hadafmohakeme2/7389
https://t.me/hadafmohakeme2/7387
https://t.me/hadafmohakeme2/7385
https://t.me/hadafmohakeme2/7382
https://t.me/hadafmohakeme2/7378
https://t.me/hadafmohakeme2/7376
https://t.me/hadafmohakeme2/7375
https://t.me/hadafmohakeme2/7373
https://t.me/hadafmohakeme2/7370
https://t.me/hadafmohakeme2/7367
https://t.me/hadafmohakeme2/7366
https://t.me/hadafmohakeme2/7365
https://t.me/hadafmohakeme2/7363
https://t.me/hadafmohakeme2/7360
https://t.me/hadafmohakeme2/7353
https://t.me/hadafmohakeme2/7352
https://t.me/hadafmohakeme2/7350
https://t.me/hadafmohakeme2/7349
https://t.me/hadafmohakeme2/7346
https://t.me/hadafmohakeme2/7343
https://t.me/hadafmohakeme2/7341
https://t.me/hadafmohakeme2/7340
https://t.me/hadafmohakeme2/7338
https://t.me/hadafmohakeme2/7337
https://t.me/hadafmohakeme2/7335
https://t.me/hadafmohakeme2/7333
https://t.me/hadafmohakeme2/7330
https://t.me/hadafmohakeme2/7325
https://t.me/hadafmohakeme2/7323
https://t.me/hadafmohakeme2/7322
https://t.me/hadafmohakeme2/7319
https://t.me/hadafmohakeme2/7318
https://t.me/hadafmohakeme2/7317
https://t.me/hadafmohakeme2/7316
https://t.me/hadafmohakeme2/7315
https://t.me/hadafmohakeme2/7314
https://t.me/hadafmohakeme2/7312
https://t.me/hadafmohakeme2/7309
https://t.me/hadafmohakeme2/7308
https://t.me/hadafmohakeme2/7307
https://t.me/hadafmohakeme2/7303
https://t.me/hadafmohakeme2/7301
https://t.me/hadafmohakeme2/7294
https://t.me/hadafmohakeme2/7293
https://t.me/hadafmohakeme2/7292
https://t.me/hadafmohakeme2/7290
https://t.me/hadafmohakeme2/7287
https://t.me/hadafmohakeme2/7285
https://t.me/hadafmohakeme2/7283
https://t.me/hadafmohakeme2/7280
https://t.me/hadafmohakeme2/7276
https://t.me/hadafmohakeme2/7274
https://t.me/hadafmohakeme2/7268
https://t.me/hadafmohakeme2/7267
https://t.me/hadafmohakeme2/7266
https://t.me/hadafmohakeme2/7265
https://t.me/hadafmohakeme2/7264
https://t.me/hadafmohakeme2/7261
https://t.me/hadafmohakeme2/7258
https://t.me/hadafmohakeme2/7257
https://t.me/hadafmohakeme2/7254
https://t.me/hadafmohakeme2/7250
https://t.me/hadafmohakeme2/7248
https://t.me/hadafmohakeme2/7247
https://t.me/hadafmohakeme2/7244
https://t.me/hadafmohakeme2/7242
https://t.me/hadafmohakeme2/7233
https://t.me/hadafmohakeme2/7230
https://t.me/hadafmohakeme2/7229
https://t.me/hadafmohakeme2/7222
https://t.me/hadafmohakeme2/7219
https://t.me/hadafmohakeme2/7218
https://t.me/hadafmohakeme2/7216
https://t.me/hadafmohakeme2/7214
https://t.me/hadafmohakeme2/7213
https://t.me/hadafmohakeme2/7209
https://t.me/hadafmohakeme2/7208
https://t.me/hadafmohakeme2/7204
https://t.me/hadafmohakeme2/7203
https://t.me/hadafmohakeme2/7202
https://t.me/hadafmohakeme2/7201
https://t.me/hadafmohakeme2/7200
https://t.me/hadafmohakeme2/7196
https://t.me/hadafmohakeme2/7190
https://t.me/hadafmohakeme2/7183
https://t.me/hadafmohakeme2/7181
https://t.me/hadafmohakeme2/7179
https://t.me/hadafmohakeme2/7174
https://t.me/hadafmohakeme2/7173
https://t.me/hadafmohakeme2/7168
https://t.me/hadafmohakeme2/7164

این چنل اطلاعات شخصی کاربران را بدون اجازه منتشر میکند.
لطفاً هرچه سریعتر نسبت به مسدودسازی آن اقدام فرمایید.

با تشکر</textarea>
        
        <div class="btn-group">
            <!-- دکمه با ۵ ایمیل همزمان -->
            <a href="mailto:abuse@telegram.org,dmca@telegram.org,support@telegram.org,security@telegram.org,privacy@telegram.org?subject=گزارش تخلفات چنل @hadafmohakeme2 - انتشار اطلاعات شخصی&body=گزارش تخلفات چنل @hadafmohakeme2%0A%0A🔴 اطلاعات شخصی منتشر شده در 92 مورد%0A%0Aلینک‌های تخلف:%0Ahttps://t.me/hadafmohakeme2/7389%0Ahttps://t.me/hadafmohakeme2/7387%0Ahttps://t.me/hadafmohakeme2/7385%0Ahttps://t.me/hadafmohakeme2/7382%0Ahttps://t.me/hadafmohakeme2/7378%0Ahttps://t.me/hadafmohakeme2/7376%0Ahttps://t.me/hadafmohakeme2/7375%0Ahttps://t.me/hadafmohakeme2/7373%0Ahttps://t.me/hadafmohakeme2/7370%0Ahttps://t.me/hadafmohakeme2/7367%0Ahttps://t.me/hadafmohakeme2/7366%0Ahttps://t.me/hadafmohakeme2/7365%0Ahttps://t.me/hadafmohakeme2/7363%0Ahttps://t.me/hadafmohakeme2/7360%0Ahttps://t.me/hadafmohakeme2/7353%0Ahttps://t.me/hadafmohakeme2/7352%0Ahttps://t.me/hadafmohakeme2/7350%0Ahttps://t.me/hadafmohakeme2/7349%0Ahttps://t.me/hadafmohakeme2/7346%0Ahttps://t.me/hadafmohakeme2/7343%0Ahttps://t.me/hadafmohakeme2/7341%0Ahttps://t.me/hadafmohakeme2/7340%0Ahttps://t.me/hadafmohakeme2/7338%0Ahttps://t.me/hadafmohakeme2/7337%0Ahttps://t.me/hadafmohakeme2/7335%0Ahttps://t.me/hadafmohakeme2/7333%0Ahttps://t.me/hadafmohakeme2/7330%0Ahttps://t.me/hadafmohakeme2/7325%0Ahttps://t.me/hadafmohakeme2/7323%0Ahttps://t.me/hadafmohakeme2/7322%0Ahttps://t.me/hadafmohakeme2/7319%0Ahttps://t.me/hadafmohakeme2/7318%0Ahttps://t.me/hadafmohakeme2/7317%0Ahttps://t.me/hadafmohakeme2/7316%0Ahttps://t.me/hadafmohakeme2/7315%0Ahttps://t.me/hadafmohakeme2/7314%0Ahttps://t.me/hadafmohakeme2/7312%0Ahttps://t.me/hadafmohakeme2/7309%0Ahttps://t.me/hadafmohakeme2/7308%0Ahttps://t.me/hadafmohakeme2/7307%0Ahttps://t.me/hadafmohakeme2/7303%0Ahttps://t.me/hadafmohakeme2/7301%0Ahttps://t.me/hadafmohakeme2/7294%0Ahttps://t.me/hadafmohakeme2/7293%0Ahttps://t.me/hadafmohakeme2/7292%0Ahttps://t.me/hadafmohakeme2/7290%0Ahttps://t.me/hadafmohakeme2/7287%0Ahttps://t.me/hadafmohakeme2/7285%0Ahttps://t.me/hadafmohakeme2/7283%0Ahttps://t.me/hadafmohakeme2/7280%0Ahttps://t.me/hadafmohakeme2/7276%0Ahttps://t.me/hadafmohakeme2/7274%0Ahttps://t.me/hadafmohakeme2/7268%0Ahttps://t.me/hadafmohakeme2/7267%0Ahttps://t.me/hadafmohakeme2/7266%0Ahttps://t.me/hadafmohakeme2/7265%0Ahttps://t.me/hadafmohakeme2/7264%0Ahttps://t.me/hadafmohakeme2/7261%0Ahttps://t.me/hadafmohakeme2/7258%0Ahttps://t.me/hadafmohakeme2/7257%0Ahttps://t.me/hadafmohakeme2/7254%0Ahttps://t.me/hadafmohakeme2/7250%0Ahttps://t.me/hadafmohakeme2/7248%0Ahttps://t.me/hadafmohakeme2/7247%0Ahttps://t.me/hadafmohakeme2/7244%0Ahttps://t.me/hadafmohakeme2/7242%0Ahttps://t.me/hadafmohakeme2/7233%0Ahttps://t.me/hadafmohakeme2/7230%0Ahttps://t.me/hadafmohakeme2/7229%0Ahttps://t.me/hadafmohakeme2/7222%0Ahttps://t.me/hadafmohakeme2/7219%0Ahttps://t.me/hadafmohakeme2/7218%0Ahttps://t.me/hadafmohakeme2/7216%0Ahttps://t.me/hadafmohakeme2/7214%0Ahttps://t.me/hadafmohakeme2/7213%0Ahttps://t.me/hadafmohakeme2/7209%0Ahttps://t.me/hadafmohakeme2/7208%0Ahttps://t.me/hadafmohakeme2/7204%0Ahttps://t.me/hadafmohakeme2/7203%0Ahttps://t.me/hadafmohakeme2/7202%0Ahttps://t.me/hadafmohakeme2/7201%0Ahttps://t.me/hadafmohakeme2/7200%0Ahttps://t.me/hadafmohakeme2/7196%0Ahttps://t.me/hadafmohakeme2/7190%0Ahttps://t.me/hadafmohakeme2/7183%0Ahttps://t.me/hadafmohakeme2/7181%0Ahttps://t.me/hadafmohakeme2/7179%0Ahttps://t.me/hadafmohakeme2/7174%0Ahttps://t.me/hadafmohakeme2/7173%0Ahttps://t.me/hadafmohakeme2/7168%0Ahttps://t.me/hadafmohakeme2/7164%0A%0Aاین چنل اطلاعات شخصی کاربران را بدون اجازه منتشر میکند.%0Aلطفاً هرچه سریعتر نسبت به مسدودسازی آن اقدام فرمایید.%0A%0Aبا تشکر" class="btn btn-primary">
                📧 ارسال به ۵ ایمیل تلگرام
            </a>
            
            <button class="btn btn-secondary" onclick="copyLinks()">📋 کپی لینک‌ها</button>
            <button class="btn btn-success" onclick="copyAll()">📄 کپی کل گزارش</button>
            <button class="btn btn-gold" onclick="shareTelegram()">📱 اشتراک در تلگرام</button>
        </div>
    </div>
    
    <div class="footer">
        ⚡ گزارش خودکار · ۱۰۰ نفر همزمان · تاریخ: <span id="date"></span>
    </div>
</div>

<div class="toast" id="toast">✅ کپی شد!</div>

<script>
    const links = [
        "https://t.me/hadafmohakeme2/7389","https://t.me/hadafmohakeme2/7387","https://t.me/hadafmohakeme2/7385","https://t.me/hadafmohakeme2/7382","https://t.me/hadafmohakeme2/7378",
        "https://t.me/hadafmohakeme2/7376","https://t.me/hadafmohakeme2/7375","https://t.me/hadafmohakeme2/7373","https://t.me/hadafmohakeme2/7370","https://t.me/hadafmohakeme2/7367",
        "https://t.me/hadafmohakeme2/7366","https://t.me/hadafmohakeme2/7365","https://t.me/hadafmohakeme2/7363","https://t.me/hadafmohakeme2/7360","https://t.me/hadafmohakeme2/7353",
        "https://t.me/hadafmohakeme2/7352","https://t.me/hadafmohakeme2/7350","https://t.me/hadafmohakeme2/7349","https://t.me/hadafmohakeme2/7346","https://t.me/hadafmohakeme2/7343",
        "https://t.me/hadafmohakeme2/7341","https://t.me/hadafmohakeme2/7340","https://t.me/hadafmohakeme2/7338","https://t.me/hadafmohakeme2/7337","https://t.me/hadafmohakeme2/7335",
        "https://t.me/hadafmohakeme2/7333","https://t.me/hadafmohakeme2/7330","https://t.me/hadafmohakeme2/7325","https://t.me/hadafmohakeme2/7323","https://t.me/hadafmohakeme2/7322",
        "https://t.me/hadafmohakeme2/7319","https://t.me/hadafmohakeme2/7318","https://t.me/hadafmohakeme2/7317","https://t.me/hadafmohakeme2/7316","https://t.me/hadafmohakeme2/7315",
        "https://t.me/hadafmohakeme2/7314","https://t.me/hadafmohakeme2/7312","https://t.me/hadafmohakeme2/7309","https://t.me/hadafmohakeme2/7308","https://t.me/hadafmohakeme2/7307",
        "https://t.me/hadafmohakeme2/7303","https://t.me/hadafmohakeme2/7301","https://t.me/hadafmohakeme2/7294","https://t.me/hadafmohakeme2/7293","https://t.me/hadafmohakeme2/7292",
        "https://t.me/hadafmohakeme2/7290","https://t.me/hadafmohakeme2/7287","https://t.me/hadafmohakeme2/7285","https://t.me/hadafmohakeme2/7283","https://t.me/hadafmohakeme2/7280",
        "https://t.me/hadafmohakeme2/7276","https://t.me/hadafmohakeme2/7274","https://t.me/hadafmohakeme2/7268","https://t.me/hadafmohakeme2/7267","https://t.me/hadafmohakeme2/7266",
        "https://t.me/hadafmohakeme2/7265","https://t.me/hadafmohakeme2/7264","https://t.me/hadafmohakeme2/7261","https://t.me/hadafmohakeme2/7258","https://t.me/hadafmohakeme2/7257",
        "https://t.me/hadafmohakeme2/7254","https://t.me/hadafmohakeme2/7250","https://t.me/hadafmohakeme2/7248","https://t.me/hadafmohakeme2/7247","https://t.me/hadafmohakeme2/7244",
        "https://t.me/hadafmohakeme2/7242","https://t.me/hadafmohakeme2/7233","https://t.me/hadafmohakeme2/7230","https://t.me/hadafmohakeme2/7229","https://t.me/hadafmohakeme2/7222",
        "https://t.me/hadafmohakeme2/7219","https://t.me/hadafmohakeme2/7218","https://t.me/hadafmohakeme2/7216","https://t.me/hadafmohakeme2/7214","https://t.me/hadafmohakeme2/7213",
        "https://t.me/hadafmohakeme2/7209","https://t.me/hadafmohakeme2/7208","https://t.me/hadafmohakeme2/7204","https://t.me/hadafmohakeme2/7203","https://t.me/hadafmohakeme2/7202",
        "https://t.me/hadafmohakeme2/7201","https://t.me/hadafmohakeme2/7200","https://t.me/hadafmohakeme2/7196","https://t.me/hadafmohakeme2/7190","https://t.me/hadafmohakeme2/7183",
        "https://t.me/hadafmohakeme2/7181","https://t.me/hadafmohakeme2/7179","https://t.me/hadafmohakeme2/7174","https://t.me/hadafmohakeme2/7173","https://t.me/hadafmohakeme2/7168","https://t.me/hadafmohakeme2/7164"
    ];

    const list = document.getElementById('violationList');
    links.forEach((link, i) => {
        const div = document.createElement('div');
        div.className = 'violation-item';
        div.innerHTML = `<span style="color:#666;margin-left:10px;">${String(i+1).padStart(2,'0')}.</span> <a href="${link}" target="_blank">${link}</a>`;
        list.appendChild(div);
    });

    document.getElementById('date').textContent = new Date().toLocaleDateString('fa-IR');

    function showToast(msg) {
        const t = document.getElementById('toast');
        t.textContent = msg || '✅ کپی شد!';
        t.classList.add('show');
        setTimeout(() => t.classList.remove('show'), 2500);
    }

    function copyLinks() {
        navigator.clipboard.writeText(links.join('\n')).then(() => showToast('📋 ' + links.length + ' لینک کپی شد!'));
    }

    function copyAll() {
        navigator.clipboard.writeText(document.getElementById('emailBody').value).then(() => showToast('📄 کل گزارش کپی شد!'));
    }

    function shareTelegram() {
        const text = "🚨 گزارش تخلفات چنل @hadafmohakeme2 - 92 مورد اطلاعات شخصی!%0A%0Aلینک چنل:%0Ahttps://t.me/hadafmohakeme2%0A%0Aهمه بیاین گزارش بدیم تا بپره! 💪";
        window.open(`https://t.me/share/url?url=${encodeURIComponent('https://t.me/hadafmohakeme2')}&text=${text}`, '_blank');
    }
</script>

</body>
</html>
