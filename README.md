
<!-- TAKI AI START -->
<style>
#taki-ai {
  direction: rtl;
  font-family: Arial, sans-serif;
  color: #183047;
  max-width: 1100px;
  margin: 30px auto;
  padding: 20px;
}
#taki-ai * { box-sizing: border-box; }
#taki-ai .ta-card {
  background: #fff;
  border: 1px solid #dce6ed;
  border-radius: 15px;
  padding: 20px;
  margin: 15px 0;
  box-shadow: 0 4px 15px #17334a0b;
}
#taki-ai h2, #taki-ai h3 { color: #123d59; }
#taki-ai label {
  display: block;
  font-weight: 600;
  margin: 12px 0 6px;
}
#taki-ai input, #taki-ai select, #taki-ai textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccd9e2;
  border-radius: 9px;
  font-size: 15px;
  background: #fff;
}
#taki-ai textarea { min-height: 85px; resize: vertical; }
#taki-ai button {
  border: 0;
  border-radius: 9px;
  padding: 12px 20px;
  margin: 8px 4px 8px 0;
  cursor: pointer;
  font-weight: bold;
  background: #087f8c;
  color: white;
}
#taki-ai button.secondary { background: #24465d; }
#taki-ai button:disabled { opacity: .5; cursor: not-allowed; }
#taki-ai .ta-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit,minmax(220px,1fr));
  gap: 12px;
}
#taki-ai .ta-section {
  border-top: 1px solid #e3ebef;
  padding-top: 12px;
  margin-top: 18px;
}
#taki-ai .ta-message {
  padding: 12px;
  border-radius: 8px;
  margin-top: 12px;
}
#taki-ai .ta-error { background: #fff0ed; color: #a52d20; }
#taki-ai .ta-success { background: #e9f8ef; color: #176b3b; }
#taki-ai .ta-patient {
  padding: 12px;
  border-bottom: 1px solid #e4ebef;
}
#taki-ai .ta-muted { color: #647987; font-size: 13px; }
#taki-ai [hidden] { display: none !important; }
</style>

<section id="taki-ai">
  <div class="ta-card">
    <h2>TAKI AI | فضاء المختص</h2>
    <p>منصة مساعدة للتقييم والمتابعة والتكفل بالأطفال والبالغين.</p>
    <p class="ta-muted">
      نسخة تجريبية. لا تدخلي بيانات مرضى حقيقية قبل استكمال إعداد الحماية.
    </p>
  </div>

  <div id="auth-panel" class="ta-card">
    <h3>دخول المختص</h3>

    <label for="taki-email">البريد الإلكتروني</label>
    <input id="taki-email" type="email" autocomplete="email">

    <label for="taki-password">كلمة المرور</label>
    <input id="taki-password" type="password" autocomplete="current-password">

    <button id="taki-login" type="button">تسجيل الدخول</button>
    <button id="taki-signup" type="button" class="secondary">إنشاء حساب</button>

    <div id="taki-auth-message" aria-live="polite"></div>
  </div>

  <div id="taki-workspace" hidden>
    <div class="ta-card">
      <div class="ta-grid">
        <div>
          <h3>فضاء المختص</h3>
          <p id="taki-user-email" class="ta-muted"></p>
        </div>
        <div>
          <button id="taki-logout" type="button" class="secondary">
            تسجيل الخروج
          </button>
        </div>
      </div>
    </div>

    <form id="taki-patient-form" class="ta-card">
      <h3>إنشاء ملف وتقييم جديد</h3>

      <div class="ta-grid">
        <div>
          <label for="taki-case-code">رمز الملف (دون اسم المريض)</label>
          <input id="taki-case-code" required maxlength="50"
                 placeholder="مثال: TAKI-002">
        </div>

        <div>
          <label for="taki-age-group">الفئة</label>
          <select id="taki-age-group" required>
            <option value="child">طفل</option>
            <option value="adult">بالغ</option>
          </select>
        </div>
      </div>

      <div class="ta-section">
        <h3>معلومات عامة</h3>

        <label>سبب الاستشارة</label>
        <textarea data-field="reason"></textarea>

        <label>تاريخ الحالة وبداية الصعوبات</label>
        <textarea data-field="history"></textarea>

        <label>نقاط القوة والقدرات</label>
        <textarea data-field="strengths"></textarea>

        <label>الصعوبات والاحتياجات الحالية</label>
        <textarea data-field="needs"></textarea>
      </div>

      <div id="taki-child-fields">
        <div class="ta-section">
          <h3>تقييم الطفل</h3>

          <label>الحمل والولادة</label>
          <textarea data-field="pregnancy_birth"></textarea>

          <label>التطور الحركي</label>
          <textarea data-field="motor_development"></textarea>

          <label>تطور اللغة والتواصل</label>
          <textarea data-field="language_development"></textarea>

          <label>الفهم والاستيعاب</label>
          <textarea data-field="comprehension"></textarea>

          <label>التعبير الشفهي واللغوي</label>
          <textarea data-field="expression"></textarea>

          <label>النطق والأصوات</label>
          <textarea data-field="speech_sounds"></textarea>

          <label>الانتباه والذاكرة</label>
          <textarea data-field="attention_memory"></textarea>

          <label>السلوك والتفاعل الاجتماعي</label>
          <textarea data-field="behavior_social"></textarea>

          <label>الأسرة والبيئة المدرسية</label>
          <textarea data-field="family_school"></textarea>

          <label>الاختبارات والملاحظات</label>
          <textarea data-field="child_tests"></textarea>
        </div>
      </div>

      <div id="taki-adult-fields" hidden>
        <div class="ta-section">
          <h3>تقييم البالغ</h3>

          <label>التاريخ الطبي والجراحي</label>
          <textarea data-field="medical_history"></textarea>

          <label>التاريخ العصبي (مثل السكتة أو الإصابة العصبية)</label>
          <textarea data-field="neurological_history"></textarea>

          <label>اللغة والكلام والصوت</label>
          <textarea data-field="language_speech_voice"></textarea>

          <label>البلع</label>
          <textarea data-field="swallowing"></textarea>

          <label>الذاكرة والانتباه والوظائف التنفيذية</label>
          <textarea data-field="cognitive_functions"></textarea>

          <label>الاستقلالية والتواصل اليومي</label>
          <textarea data-field="daily_life_communication"></textarea>

          <label>الاختبارات والملاحظات</label>
          <textarea data-field="adult_tests"></textarea>
        </div>
      </div>

      <div class="ta-section">
        <h3>التقييم الأولي وخطة المتابعة</h3>

        <label>الملاحظات السريرية للمختص</label>
        <textarea data-field="clinical_observations"></textarea>

        <label>الأهداف الأولية المقترحة</label>
        <textarea data-field="initial_goals"
                  placeholder="أهداف واضحة وقابلة للقياس والمراجعة"></textarea>

        <label>ملاحظات إضافية</label>
        <textarea data-field="additional_notes"></textarea>
      </div>

      <button id="taki-save-patient" type="submit">
        حفظ الملف والتقييم
      </button>

      <div id="taki-save-message" aria-live="polite"></div>
    </form>

    <div class="ta-card">
      <h3>ملفات المختص</h3>
      <button id="taki-refresh-patients" type="button" class="secondary">
        تحديث القائمة
      </button>
      <div id="taki-patient-list"></div>
    </div>
  </div>
</section>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<script>
(function () {
  "use strict";

  const SUPABASE_URL =
    "https://uplrnpbtelciryfjgnsk.supabase.co";

  const SUPABASE_KEY =
    "sb_publishable_MpOqik1SWcq63khOem_unA_IA2eUL5i";

  const root = document.getElementById("taki-ai");

  if (!root || !window.supabase) {
    console.error("TAKI AI: Supabase library is not available.");
    return;
  }

  const db = window.supabase.createClient(
    SUPABASE_URL,
    SUPABASE_KEY
  );

  const $ = function (id) {
    return root.querySelector("#" + id);
  };

  const authPanel = $("auth-panel");
  const workspace = $("taki-workspace");
  const authMessage = $("taki-auth-message");
  const saveMessage = $("taki-save-message");
  const patientForm = $("taki-patient-form");
  const saveButton = $("taki-save-patient");

  let currentUser = null;

  function showMessage(element, text, isError) {
    element.textContent = text;
    element.className =
      "ta-message " + (isError ? "ta-error" : "ta-success");
  }

  function clearMessage(element) {
    element.textContent = "";
    element.className = "";
  }

  function showWorkspace(user) {
    currentUser = user || null;

    if (user) {
      authPanel.hidden = true;
      workspace.hidden = false;
      $("taki-user-email").textContent = user.email || "";
      loadPatients();
    } else {
      authPanel.hidden = false;
      workspace.hidden = true;
      $("taki-user-email").textContent = "";
    }
  }

  function updateAgeFields() {
    const type = $("taki-age-group").value;

    $("taki-child-fields").hidden = type !== "child";
    $("taki-adult-fields").hidden = type !== "adult";
  }

  $("taki-age-group").addEventListener("change", updateAgeFields);
  updateAgeFields();

  $("taki-signup").addEventListener("click", async function () {
    clearMessage(authMessage);

    const email = $("taki-email").value.trim();
    const password = $("taki-password").value;

    if (!email || password.length < 6) {
      showMessage(
        authMessage,
        "أدخلي بريداً إلكترونياً وكلمة مرور من 6 أحرف على الأقل.",
        true
      );
      return;
    }

    $("taki-signup").disabled = true;

    const { data, error } = await db.auth.signUp({
      email: email,
      password: password
    });

    $("taki-signup").disabled = false;

    if (error) {
      showMessage(authMessage, error.message, true);
      return;
    }

    if (data.session) {
      showMessage(authMessage, "تم إنشاء الحساب.", false);
    } else {
      showMessage(
        authMessage,
        "تم إنشاء الحساب. افتحي بريدك الإلكتروني لتأكيد الحساب، ثم سجّلي الدخول.",
        false
      );
    }
  });

  $("taki-login").addEventListener("click", async function () {
    clearMessage(authMessage);

    const email = $("taki-email").value.trim();
    const password = $("taki-password").value;

    if (!email || !password) {
      showMessage(authMessage, "أدخلي البريد الإلكتروني وكلمة المرور.", true);
      return;
    }

    $("taki-login").disabled = true;

    const { error } = await db.auth.signInWithPassword({
      email: email,
      password: password
    });

    $("taki-login").disabled = false;

    if (error) {
      showMessage(authMessage, error.message, true);
    }
  });

  $("taki-logout").addEventListener("click", async function () {
    const { error } = await db.auth.signOut();

    if (error) {
      showMessage(authMessage, error.message, true);
    }
  });

  async function loadPatients() {
    const list = $("taki-patient-list");

    list.textContent = "جارٍ تحميل الملفات...";

    const { data, error } = await db
      .from("patients")
      .select("id, case_code, age_group, created_at")
      .order("created_at", { ascending: false });

    if (error) {
      list.textContent = "تعذر تحميل الملفات: " + error.message;
      return;
    }

    list.replaceChildren();

    if (!data || data.length === 0) {
      list.textContent = "لا توجد ملفات محفوظة حتى الآن.";
      return;
    }

    data.forEach(function (patient) {
      const item = document.createElement("div");
      item.className = "ta-patient";

      const title = document.createElement("strong");
      title.textContent = patient.case_code;

      const details = document.createElement("p");
      details.className = "ta-muted";
      details.textContent =
        (patient.age_group === "child" ? "طفل" : "بالغ") +
        " — " +
        new Date(patient.created_at).toLocaleDateString();

      item.appendChild(title);
      item.appendChild(details);
      list.appendChild(item);
    });
  }

  $("taki-refresh-patients").addEventListener("click", loadPatients);

  patientForm.addEventListener("submit", async function (event) {
    event.preventDefault();
    clearMessage(saveMessage);

    if (!currentUser) {
      showMessage(saveMessage, "يجب تسجيل الدخول أولاً.", true);
      return;
    }

    const caseCode = $("taki-case-code").value.trim();
    const ageGroup = $("taki-age-group").value;

    if (!caseCode) {
      showMessage(saveMessage, "أدخلي رمز الملف أولاً.", true);
      return;
    }

    const clinicalData = {};

    root.querySelectorAll("[data-field]").forEach(function (field) {
      clinicalData[field.dataset.field] = field.value.trim();
    });

    saveButton.disabled = true;
    saveButton.textContent = "جارٍ الحفظ...";

    try {
      const { data: patient, error: patientError } = await db
        .from("patients")
        .insert({
          case_code: caseCode,
          age_group: ageGroup
        })
        .select()
        .single();

      if (patientError) {
        throw new Error(
          "لم يتم إنشاء الملف. قد يكون رمز الملف مستعملاً من قبل. التفاصيل: " +
          patientError.message
        );
      }

      const { error: assessmentError } = await db
        .from("assessments")
        .insert({
          patient_id: patient.id,
          clinical_data: clinicalData
        });

      if (assessmentError) {
        showMessage(
          saveMessage,
          "تم حفظ الملف الأساسي، لكن فشل حفظ التقييم. لا تعيدي إنشاء الملف بالرمز نفسه. التفاصيل: " +
          assessmentError.message,
          true
        );
        await loadPatients();
        return;
      }

      showMessage(
        saveMessage,
        "تم حفظ الملف والتقييم بنجاح.",
        false
      );

      patientForm.reset();
      updateAgeFields();
      await loadPatients();

    } catch (error) {
      showMessage(saveMessage, error.message, true);
    } finally {
      saveButton.disabled = false;
      saveButton.textContent = "حفظ الملف والتقييم";
    }
  });

  db.auth.onAuthStateChange(function (event, session) {
    showWorkspace(session ? session.user : null);
  });

  db.auth.getSession().then(function (result) {
    if (result.error) {
      showMessage(authMessage, result.error.message, true);
      return;
    }

    showWorkspace(
      result.data.session ? result.data.session.user : null
    );
  });
})();
</script>
<!-- TAKI AI END -->
