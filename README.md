<!DOCTYPE html>
<html lang="fa" dir="rtl">

<head>
  <meta charset="UTF-8">

  <meta name="viewport"
        content="width=device-width,
        initial-scale=1,
        maximum-scale=1,
        user-scalable=no,
        viewport-fit=cover">

  <meta name="theme-color" content="#1976D2">
  <meta name="mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="default">
  <meta name="apple-mobile-web-app-title" content="لیست خرید">

  <link rel="manifest" href="manifest.json">

  <title>لیست خرید</titfile:///data/user/0/com.foxdebug.acodefree/files/public/Index.htmlle>

  <style>

    * {
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
    }

    html,
    body {
      margin: 0;
      padding: 0;
      min-height: 100%;
      font-family:
        Tahoma,
        Arial,
        sans-serif;
      background: #f5f7fb;
      color: #172033;
    }

    body {
      padding-bottom: env(safe-area-inset-bottom);
    }

    button,
    input {
      font-family: inherit;
    }

    button {
      cursor: pointer;
    }

    /* Header */

    .header {
      position: sticky;
      top: 0;
      z-index: 20;

      background: rgba(255,255,255,.96);

      backdrop-filter: blur(12px);

      padding:
        calc(14px + env(safe-area-inset-top))
        14px
        12px;

      border-bottom: 1px solid #e9edf3;
    }

    .header-title {
      display: flex;
      align-items: center;
      justify-content: space-between;

      margin-bottom: 12px;
    }

    .header-title h1 {
      margin: 0;

      font-size: 22px;
      font-weight: 800;
    }

    .header-actions {
      display: flex;
      gap: 6px;
    }

    .icon-button {
      width: 40px;
      height: 40px;

      border: none;
      border-radius: 12px;

      background: #f1f4f8;

      font-size: 18px;
    }

    .search-box {
      position: relative;
    }

    .search-box input {
      width: 100%;

      border: 1px solid #e1e6ee;
      border-radius: 15px;

      padding: 13px 44px 13px 42px;

      background: #f8fafc;

      outline: none;

      font-size: 15px;
    }

    .search-icon {
      position: absolute;

      right: 14px;
      top: 50%;

      transform: translateY(-50%);

      color: #7b8492;
    }

    .clear-search {
      position: absolute;

      left: 8px;
      top: 50%;

      transform: translateY(-50%);

      border: none;
      background: transparent;

      font-size: 18px;

      color: #7b8492;
    }

    /* Main */

    .main {
      padding: 12px 12px 110px;
    }

    /* Category */

    .category {
      background: white;

      border-radius: 19px;

      margin-bottom: 11px;

      overflow: hidden;

      box-shadow:
        0 3px 18px rgba(0,0,0,.055);
    }

    .category-header {
      display: flex;

      align-items: center;

      gap: 11px;

      padding: 14px;

      user-select: none;
    }

    .category-header:active {
      background: #fafbfd;
    }

    .category-icon {
      width: 45px;
      height: 45px;

      display: flex;
      align-items: center;
      justify-content: center;

      border-radius: 14px;

      background: #eaf3ff;

      font-size: 22px;
    }

    .category-info {
      flex: 1;
    }

    .category-name {
      font-weight: 800;
      font-size: 16px;
    }

    .category-count {
      color: #7a8290;

      font-size: 12px;

      margin-top: 4px;
    }

    .category-arrow {
      font-size: 19px;

      transition: .2s;
    }

    .category.open
    .category-arrow {
      transform: rotate(180deg);
    }

    .category-items {
      display: none;

      border-top: 1px solid #eef1f5;
    }

    .category.open
    .category-items {
      display: block;
    }

    /* Item */

    .item {
      display: flex;

      align-items: center;

      gap: 8px;

      min-height: 60px;

      padding: 8px 12px;

      border-bottom: 1px solid #f0f2f5;
    }

    .item:last-of-type {
      border-bottom: none;
    }

    .item-checkbox {
      width: 22px;
      height: 22px;

      accent-color: #1976d2;

      flex-shrink: 0;
    }

    .item-content {
      flex: 1;

      min-width: 0;
    }

    .item-name {
      font-size: 15px;
      font-weight: 600;
    }

    .item.checked
    .item-name {
      text-decoration: line-through;

      color: #9299a5;
    }

    .item-meta {
      display: block;

      color: #7b8490;

      font-size: 11px;

      margin-top: 4px;
    }

    .item-button {
      width: 36px;
      height: 36px;

      border: none;

      background: transparent;

      border-radius: 10px;

      font-size: 17px;
    }

    .item-button:active {
      background: #f1f4f8;
    }

    .delete-button {
      color: #d83b3b;
    }

    .add-item {
      width: 100%;

      border: none;

      background: #f8fafc;

      color: #1976d2;

      font-size: 14px;

      font-weight: 800;

      padding: 14px;
    }

    /* Bottom */

    .bottom-bar {
      position: fixed;

      left: 0;
      right: 0;
      bottom: 0;

      z-index: 30;

      background: rgba(255,255,255,.97);

      backdrop-filter: blur(12px);

      padding:
        10px
        12px
        calc(10px + env(safe-area-inset-bottom));

      box-shadow:
        0 -4px 18px rgba(0,0,0,.08);
    }

    .primary-button {
      width: 100%;

      height: 54px;

      border: none;

      border-radius: 16px;

      background: #1976d2;

      color: white;

      font-size: 15px;

      font-weight: 800;
    }

    .primary-button:disabled {
      opacity: .45;

      cursor: default;
    }

    /* Modal */

    .modal {
      position: fixed;

      inset: 0;

      z-index: 100;

      display: none;

      align-items: flex-end;

      background: rgba(0,0,0,.52);
    }

    .modal.show {
      display: flex;
    }

    .modal-sheet {
      width: 100%;

      max-height: 90vh;

      overflow-y: auto;

      background: white;

      border-radius:
        23px
        23px
        0
        0;

      padding:
        20px
        16px
        calc(20px + env(safe-area-inset-bottom));
    }

    .modal-title {
      margin: 0 0 18px;

      font-size: 19px;
      font-weight: 800;
    }

    .field {
      width: 100%;

      padding: 13px;

      margin-bottom: 10px;

      border: 1px solid #dfe4eb;

      border-radius: 13px;

      outline: none;

      font-size: 14px;
    }

    .field:focus {
      border-color: #1976d2;
    }

    .modal-actions {
      display: flex;

      gap: 9px;

      margin-top: 8px;
    }

    .modal-button {
      flex: 1;

      border: none;

      padding: 13px;

      border-radius: 13px;

      font-weight: 800;
    }

    .cancel-button {
      background: #eef1f5;
    }

    .save-button {
      background: #1976d2;
      color: white;
    }

    /* Final List */

    .final-header {
      display: flex;

      align-items: center;

      gap: 8px;

      padding:
        calc(14px + env(safe-area-inset-top))
        14px
        14px;

      background: white;

      border-bottom: 1px solid #e9edf3;
    }

    .back-button {
      border: none;

      background: #f1f4f8;

      width: 40px;
      height: 40px;

      border-radius: 12px;

      font-size: 18px;
    }

    .final-title {
      font-weight: 800;

      font-size: 20px;
    }

    .final-main {
      padding: 12px 12px 110px;
    }

    .final-category {
      color: #1976d2;

      font-size: 16px;

      font-weight: 800;

      margin:
        16px 4px 8px;
    }

    .final-item {
      background: white;

      padding: 13px;

      margin-bottom: 7px;

      border-radius: 13px;

      box-shadow:
        0 2px 10px rgba(0,0,0,.04);
    }

    .final-note {
      display: block;

      color: #7b8490;

      font-size: 11px;

      margin-top: 5px;
    }

    .empty {
      text-align: center;

      color: #7b8490;

      padding: 70px 20px;
    }

    /* Toast */

    .toast {
      position: fixed;

      z-index: 200;

      bottom: 90px;

      left: 50%;

      transform:
        translateX(-50%)
        translateY(20px);

      background: #20242b;

      color: white;

      padding: 11px 17px;

      border-radius: 12px;

      font-size: 13px;

      opacity: 0;

      pointer-events: none;

      transition: .25s;
    }

    .toast.show {
      opacity: 1;

      transform:
        translateX(-50%)
        translateY(0);
    }

  </style>
</head>

<body>

<div id="app"></div>

<div id="modal"
     class="modal">

  <div class="modal-sheet">

    <h2 id="modalTitle"
        class="modal-title">
      افزودن کالا
    </h2>

    <input id="itemName"
           class="field"
           type="text"
           placeholder="نام کالا">

    <input id="itemQuantity"
           class="field"
           type="text"
           placeholder="مقدار / تعداد">

    <input id="itemNote"
           class="field"
           type="text"
           placeholder="یادداشت اختیاری">

    <div class="modal-actions">

      <button class="modal-button cancel-button"
              onclick="closeModal()">
        انصراف
      </button>

      <button class="modal-button save-button"
              onclick="saveItem()">
        ذخیره
      </button>

    </div>

  </div>

</div>

<div id="toast"
     class="toast">
</div>

<script>

const STORAGE_KEY = "shopping_list_pwa_v1";

const categoriesInfo = {

  "پروتئین": "🥩",

  "سوپرمارکت": "🛒",

  "عطاری": "🌿",

  "پلاستیک‌فروشی": "📦",

  "نان": "🍞"

};

const defaultItems = {

  "پروتئین": [
    "مرغ",
    "سینه مرغ",
    "ران مرغ",
    "گوشت گوسفندی",
    "گوشت گوساله",
    "گوشت چرخ‌کرده",
    "ماهی",
    "میگو",
    "تخم‌مرغ"
  ],

  "سوپرمارکت": [
    "شیر",
    "ماست",
    "پنیر",
    "کره",
    "خامه",
    "برنج",
    "ماکارونی",
    "رب گوجه",
    "روغن",
    "شکر",
    "نمک",
    "چای",
    "قهوه",
    "نوشابه",
    "آب معدنی",
    "بیسکویت",
    "تنقلات"
  ],

  "عطاری": [
    "زعفران",
    "گل محمدی",
    "دارچین",
    "هل",
    "زنجبیل",
    "زردچوبه",
    "فلفل سیاه",
    "آویشن",
    "نعناع خشک",
    "گل گاوزبان",
    "چای سبز",
    "عسل"
  ],

  "پلاستیک‌فروشی": [
    "کیسه زباله",
    "کیسه فریزر",
    "سفره یکبار مصرف",
    "ظروف یکبار مصرف",
    "لیوان یکبار مصرف",
    "بشقاب یکبار مصرف",
    "ظرف غذا",
    "دستکش یکبار مصرف",
    "سلفون",
    "فویل آلومینیومی"
  ],

  "نان": [
    "نان سنگک",
    "نان بربری",
    "نان لواش",
    "نان تافتون",
    "نان تست",
    "نان باگت"
  ]

};

let data = loadData();

let editingCategory = null;
let editingIndex = null;

let searchText = "";

function createDefaultData() {

  const result = {};

  Object.entries(defaultItems).forEach(
    ([category, items]) => {

      result[category] = items.map(
        name => ({
          name,
          quantity: "",
          note: "",
          checked: false
        })
      );

    }
  );

  return result;
}

function loadData() {

  try {

    const saved =
      localStorage.getItem(STORAGE_KEY);

    if (saved) {

      return JSON.parse(saved);

    }

  } catch (error) {

    console.error(error);

  }

  return createDefaultData();
}

function saveData() {

  localStorage.setItem(
    STORAGE_KEY,
    JSON.stringify(data)
  );

}

function escapeHtml(value) {

  return String(value)
    .replaceAll("&", "&amp;")
    .replaceAll("<", "&lt;")
    .replaceAll(">", "&gt;")
    .replaceAll('"', "&quot;")
    .replaceAll("'", "&#039;");

}

function getSelectedItems() {

  const result = [];

  Object.entries(data).forEach(
    ([category, items]) => {

      items.forEach(item => {

        if (item.checked) {

          result.push({
            category,
            ...item
          });

        }

      });

    }
  );

  return result;

}

function selectedCount() {

  return getSelectedItems().length;

}

function renderHome() {

  let html = `

    <header class="header">

      <div class="header-title">

        <h1>
          🛒 لیست خرید
        </h1>

        <div class="header-actions">

          <button
            class="icon-button"
            onclick="clearChecks()"
            title="پاک کردن انتخاب‌ها">

            🧹

          </button>

        </div>

      </div>

      <div class="search-box">

        <span class="search-icon">
          🔍
        </span>

        <input
          id="searchInput"
          value="${escapeHtml(searchText)}"
          placeholder="جستجوی کالا..."
          oninput="handleSearch(this.value)">

        ${
          searchText
          ? `
            <button
              class="clear-search"
              onclick="clearSearch()">
              ×
            </button>
          `
          : ""
        }

      </div>

    </header>

    <main class="main">
  `;

  let hasResults = false;

  Object.entries(data).forEach(
    ([category, items]) => {

      const visibleItems =
        items.filter(
          item =>
            !searchText ||
            item.name.includes(searchText)
        );

      if (
        searchText &&
        visibleItems.length === 0
      ) {
        return;
      }

      hasResults = true;

      const checked =
        items.filter(
          item => item.checked
        ).length;

      html += `

        <section
          class="category"
          id="category-${escapeHtml(category)}">

          <div
            class="category-header"
            onclick="toggleCategory('${escapeHtml(category)}')">

            <div class="category-icon">
              ${categoriesInfo[category] || "🛍️"}
            </div>

            <div class="category-info">

              <div class="category-name">
                ${escapeHtml(category)}
              </div>

              <div class="category-count">

                ${
                  checked
                  ? `${checked} مورد انتخاب شده`
                  : `${items.length} کالا`
                }

              </div>

            </div>

            <div class="category-arrow">
              ⌄
            </div>

          </div>

          <div class="category-items">

      `;

      visibleItems.forEach(
        item => {

          const realIndex =
            items.indexOf(item);

          const meta = [];

          if (item.quantity) {

            meta.push(
              `مقدار: ${escapeHtml(item.quantity)}`
            );

          }

          if (item.note) {

            meta.push(
              escapeHtml(item.note)
            );

          }

          html += `

            <div
              class="item ${item.checked ? "checked" : ""}">

              <input
                class="item-checkbox"
                type="checkbox"
                ${
                  item.checked
                  ? "checked"
                  : ""
                }
                onchange="
                  toggleItem(
                    '${escapeHtml(category)}',
                    ${realIndex}
                  )
                ">

              <div class="item-content">

                <div class="item-name">
                  ${escapeHtml(item.name)}
                </div>

                ${
                  meta.length
                  ? `
                    <span class="item-meta">
                      ${meta.join(" • ")}
                    </span>
                  `
                  : ""
                }

              </div>

              <button
                class="item-button"
                onclick="
                  openEdit(
                    '${escapeHtml(category)}',
                    ${realIndex}
                  )
                ">
                ✏️
              </button>

              <button
                class="item-button delete-button"
                onclick="
                  deleteItem(
                    '${escapeHtml(category)}',
                    ${realIndex}
                  )
                ">
                🗑️
              </button>

            </div>

          `;

        }
      );

      html += `

            <button
              class="add-item"
              onclick="
                openAdd('${escapeHtml(category)}')
              ">

              ＋ افزودن کالا

            </button>

          </div>

        </section>

      `;

    }
  );

  if (!hasResults) {

    html += `

      <div class="empty">

        کالایی با این نام پیدا نشد.

      </div>

    `;

  }

  html += `

    </main>

    <div class="bottom-bar">

      <button
        class="primary-button"
        ${
          selectedCount() === 0
          ? "disabled"
          : ""
        }
        onclick="showFinalList()">

        ${
          selectedCount()
          ? `🛒 ساخت لیست خرید
             (${selectedCount()} مورد)`
          : "🛒 ساخت لیست خرید"
        }

      </button>

    </div>

  `;

  document.getElementById("app").innerHTML =
    html;

}

function handleSearch(value) {

  searchText = value.trim();

  renderHome();

}

function clearSearch() {

  searchText = "";

  renderHome();

}

function toggleCategory(category) {

  const element =
    document.getElementById(
      "category-" + category
    );

  if (element) {

    element.classList.toggle("open");

  }

}

function toggleItem(category, index) {

  data[category][index].checked =
    !data[category][index].checked;

  saveData();

  renderHome();

}

function clearChecks() {

  if (selectedCount() === 0) {

    showToast(
      "موردی انتخاب نشده است."
    );

    return;

  }

  const confirmed =
    confirm(
      "تیک تمام کالاهای انتخاب‌شده پاک شود؟"
    );

  if (!confirmed) return;

  Object.values(data).forEach(
    items => {

      items.forEach(
        item => item.checked = false
      );

    }
  );

  saveData();

  renderHome();

}

function openAdd(category) {

  editingCategory = category;

  editingIndex = null;

  document.getElementById(
    "modalTitle"
  ).textContent =
    "افزودن کالا";

  document.getElementById(
    "itemName"
  ).value = "";

  document.getElementById(
    "itemQuantity"
  ).value = "";

  document.getElementById(
    "itemNote"
  ).value = "";

  document
    .getElementById("modal")
    .classList.add("show");

  setTimeout(
    () =>
      document
        .getElementById("itemName")
        .focus(),
    100
  );

}

function openEdit(category, index) {

  const item =
    data[category][index];

  editingCategory = category;

  editingIndex = index;

  document.getElementById(
    "modalTitle"
  ).textContent =
    "ویرایش کالا";

  document.getElementById(
    "itemName"
  ).value =
    item.name;

  document.getElementById(
    "itemQuantity"
  ).value =
    item.quantity;

  document.getElementById(
    "itemNote"
  ).value =
    item.note;

  document
    .getElementById("modal")
    .classList.add("show");

}

function closeModal() {

  document
    .getElementById("modal")
    .classList.remove("show");

}

function saveItem() {

  const name =
    document
      .getElementById("itemName")
      .value
      .trim();

  if (!name) {

    showToast(
      "نام کالا را وارد کنید."
    );

    return;

  }

  const quantity =
    document
      .getElementById("itemQuantity")
      .value
      .trim();

  const note =
    document
      .getElementById("itemNote")
      .value
      .trim();

  if (editingIndex === null) {

    data[editingCategory].push({

      name,
      quantity,
      note,
      checked: false

    });

  } else {

    const old =
      data[
        editingCategory
      ][editingIndex];

    data[
      editingCategory
    ][editingIndex] = {

      name,
      quantity,
      note,
      checked: old.checked

    };

  }

  saveData();

  closeModal();

  renderHome();

  showToast(
    "کالا ذخیره شد."
  );

}

function deleteItem(category, index) {

  const item =
    data[category][index];

  if (
    !confirm(
      `«${item.name}» حذف شود؟`
    )
  ) {

    return;

  }

  data[category].splice(
    index,
    1
  );

  saveData();

  renderHome();

  showToast(
    "کالا حذف شد."
  );

}

function showFinalList() {

  const selected =
    getSelectedItems();

  if (!selected.length) {

    showToast(
      "هنوز کالایی انتخاب نشده است."
    );

    return;

  }

  let html = `

    <div class="final-header">

      <button
        class="back-button"
        onclick="renderHome()">

        ←

      </button>

      <div class="final-title">
        لیست نهایی خرید
      </div>

    </div>

    <main class="final-main">

  `;

  let currentCategory = null;

  selected.forEach(item => {

    if (
      currentCategory !==
      item.category
    ) {

      currentCategory =
        item.category;

      html += `

        <div class="final-category">

          ${
            categoriesInfo[
              item.category
            ] || "🛍️"
          }

          ${escapeHtml(
            item.category
          )}

        </div>

      `;

    }

    const details = [];

    if (item.quantity) {

      details.push(
        `مقدار: ${escapeHtml(item.quantity)}`
      );

    }

    if (item.note) {

      details.push(
        escapeHtml(item.note)
      );

    }

    html += `

      <div class="final-item">

        ☑️
        ${escapeHtml(item.name)}

        ${
          details.length
          ? `
            <span class="final-note">
              ${details.join(" • ")}
            </span>
          `
          : ""
        }

      </div>

    `;

  });

  html += `

    </main>

    <div class="bottom-bar">

      <button
        class="primary-button"
        onclick="shareList()">

        📤 ارسال لیست

      </button>

    </div>

  `;

  document.getElementById("app").innerHTML =
    html;

}

function createShareText() {

  const selected =
    getSelectedItems();

  let text =
    "🛒 لیست خرید\n\n";

  let currentCategory = null;

  selected.forEach(item => {

    if (
      currentCategory !==
      item.category
    ) {

      currentCategory =
        item.category;

      text +=
        `📌 ${item.category}\n`;

    }

    text +=
      `☐ ${item.name}`;

    if (item.quantity) {

      text +=
        ` — ${item.quantity}`;

    }

    if (item.note) {

      text +=
        ` (${item.note})`;

    }

    text += "\n";

  });

  text +=
    `\nتعداد موارد: ${selected.length}`;

  return text;

}

async function shareList() {

  const text =
    createShareText();

  if (
    navigator.share
  ) {

    try {

      await navigator.share({

        title: "لیست خرید",

        text: text

      });

    } catch (error) {

      console.log(
        "Share cancelled"
      );

    }

  } else {

    try {

      await navigator.clipboard.writeText(
        text
      );

      showToast(
        "لیست کپی شد."
      );

    } catch {

      alert(text);

    }

  }

}

function showToast(message) {

  const toast =
    document.getElementById(
      "toast"
    );

  toast.textContent =
    message;

  toast.classList.add(
    "show"
  );

  setTimeout(
    () => {

      toast.classList.remove(
        "show"
      );

    },
    2200
  );

}

/* Modal close by tapping outside */

document
  .getElementById("modal")
  .addEventListener(
    "click",
    event => {

      if (
        event.target.id ===
        "modal"
      ) {

        closeModal();

      }

    }
  );

/* Enter key in name field */

document
  .getElementById("itemName")
  .addEventListener(
    "keydown",
    event => {

      if (
        event.key === "Enter"
      ) {

        saveItem();

      }

    }
  );

/* PWA */

if (
  "serviceWorker" in navigator
) {

  window.addEventListener(
    "load",
    () => {

      navigator.serviceWorker
        .register("sw.js")
        .catch(
          error =>
            console.log(
              "Service Worker:",
              error
            )
        );

    }
  );

}

renderHome();

</script>

</body>
</html> Shopping-list
Raz

{
  "name": "لیست خرید",
  "short_name": "لیست خرید",
  "description": "اپلیکیشن ساده و حرفه‌ای برای مدیریت لیست خرید",
  "start_url": "./",
  "display": "standalone",
  "orientation": "portrait",
  "background_color": "#F5F7FB",
  "theme_color": "#1976D2",
  "lang": "fa",
  "dir": "rtl"
}
