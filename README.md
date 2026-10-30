<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>菜谱详情 · 食谱集</title>
  <meta name="description" content="查看菜谱的用料清单与完整分步做法。" />
  <link rel="stylesheet" href="css/base.css" />
  <link rel="stylesheet" href="css/components.css" />
  <link rel="stylesheet" href="css/layout.css" />
</head>
<body>
  <header class="site-nav">
    <div class="container site-nav__inner">
      <div class="detail-nav__left">
        <a class="btn btn--ghost btn--sm" href="index.html">
          <span class="btn__icon" aria-hidden="true"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 12H5" /><path d="M12 19l-7-7 7-7" /></svg></span>
          返回
        </a>
        <span class="detail-nav__title" id="navTitle">菜谱详情</span>
      </div>
      <div class="site-nav__actions">
        <a class="btn btn--ghost btn--sm" id="editBtn" href="edit.html">
          <span class="btn__icon" aria-hidden="true"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.9" stroke-linecap="round" stroke-linejoin="round"><path d="M12 20h9" /><path d="M16.5 3.5a2.12 2.12 0 013 3L7 19l-4 1 1-4z" /></svg></span>
          编辑
        </a>
        <button class="btn btn--danger btn--sm hidden" type="button" id="deleteBtn">
          <span class="btn__icon" aria-hidden="true"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.9" stroke-linecap="round" stroke-linejoin="round"><path d="M3 6h18" /><path d="M8 6V4h8v2" /><path d="M19 6l-1 14a2 2 0 01-2 2H8a2 2 0 01-2-2L5 6" /></svg></span>
          删除
        </button>
        <a class="btn btn--primary btn--sm" href="edit.html">新建菜谱</a>
      </div>
    </div>
  </header>

  <main class="page-main">
    <div class="container">
      <nav class="breadcrumb" aria-label="位置导航">
        <a href="index.html">全部菜谱</a>
        <span aria-hidden="true">/</span>
        <span id="crumbTitle">菜谱详情</span>
      </nav>

      <article id="detailRoot" class="hidden">
        <!-- 封面区 -->
        <header class="detail-hero">
          <div id="heroMedia"></div>
          <div class="detail-hero__content">
            <div class="detail-hero__meta" id="heroMeta"></div>
            <h1 class="detail-hero__title" id="detailTitle"></h1>
            <p class="detail-hero__desc" id="detailDesc"></p>
          </div>
        </header>

        <div class="detail-body">
          <!-- 左侧主内容 -->
          <div class="detail-main">
            <section class="detail-block">
              <h2 class="detail-block__title"><span class="dot" aria-hidden="true"></span>用料清单</h2>
              <table class="ingredient-table">
                <caption class="sr-only">这道菜需要的全部食材与用量</caption>
                <tbody id="ingredientBody"></tbody>
              </table>
            </section>

            <section class="detail-block">
              <h2 class="detail-block__title">
                <span class="dot" aria-hidden="true"></span>做菜步骤
                <span class="section-sub" id="stepCount"></span>
              </h2>
              <ol class="steps-timeline" id="stepsTimeline"></ol>
            </section>

            <section class="detail-block hidden" id="tipsBlock">
              <h2 class="detail-block__title"><span class="dot" aria-hidden="true"></span>小贴士</h2>
              <p id="tipsText"></p>
            </section>
          </div>

          <!-- 右侧信息栏 -->
          <aside class="detail-side">
            <div class="detail-block">
              <div class="meta-bar" id="metaBar"></div>
            </div>

            <div class="detail-block">
              <div class="tag-row" id="tagRow"></div>
              <p class="detail-note" id="detailNote"></p>
            </div>

            <div class="detail-block">
              <div class="detail-actions">
                <a class="btn btn--primary" id="editBtnAside" href="edit.html">编辑这道菜</a>
                <a class="btn btn--ghost" href="index.html">返回全部菜谱</a>
                <button class="btn btn--danger hidden" type="button" id="deleteBtnAside">删除这道菜</button>
              </div>
            </div>
          </aside>
        </div>
      </article>

      <!-- 未找到 -->
      <div class="empty-state hidden" id="notFound">
        <div class="empty-state__art" aria-hidden="true">🍚</div>
        <h2 class="empty-state__title">没有找到这道菜谱</h2>
        <p class="empty-state__text">它可能已经被删除，或者链接不完整。</p>
        <a class="btn btn--primary" href="index.html">返回全部菜谱</a>
      </div>
    </div>
  </main>

  <footer class="site-footer">
    <div class="container site-footer__inner">
      <p class="site-footer__text">食谱集 · 数据保存在本机浏览器中，双击即可离线使用。</p>
      <div class="site-footer__actions">
        <a class="btn btn--ghost btn--sm" href="index.html">全部菜谱</a>
        <a class="btn btn--primary btn--sm" href="edit.html">新建菜谱</a>
      </div>
    </div>
  </footer>

  <script src="js/data/recipes.js"></script>
  <script src="js/utils.js"></script>
  <script src="js/storage.js"></script>
  <script src="js/detail.js"></script>
</body>
</html>

<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>新建菜谱 · 食谱集</title>
  <meta name="description" content="录入自己的菜谱：填写用料与分步做法，上传封面图与步骤图。" />
  <link rel="stylesheet" href="css/base.css" />
  <link rel="stylesheet" href="css/components.css" />
  <link rel="stylesheet" href="css/layout.css" />
</head>
<body>
  <header class="site-nav">
    <div class="container site-nav__inner">
      <div class="detail-nav__left">
        <a class="btn btn--ghost btn--sm" href="index.html" id="backBtn">
          <span class="btn__icon" aria-hidden="true"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 12H5" /><path d="M12 19l-7-7 7-7" /></svg></span>
          返回
        </a>
        <span class="detail-nav__title" id="pageTitle">新建菜谱</span>
      </div>
      <div class="site-nav__actions">
        <button class="btn btn--primary btn--sm" type="submit" form="recipeForm" id="saveBtnTop">
          <span class="btn__icon" aria-hidden="true"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6.5L9.5 17 4 11.5" /></svg></span>
          保存
        </button>
      </div>
    </div>
  </header>

  <main class="page-main form-page">
    <div class="container">
      <div class="form-error-summary" id="errorSummary" role="alert">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.9" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M12 3.5l9.5 16.5H2.5z" /><path d="M12 9.5v4.5" /><circle cx="12" cy="17" r="0.6" fill="currentColor" /></svg>
        <span id="errorSummaryText"></span>
      </div>

      <form class="form-layout" id="recipeForm" novalidate>
        <!-- ============ 左侧主表单 ============ -->
        <div class="form-main">
          <!-- 基本信息 -->
          <section class="form-card">
            <div class="form-card__head">
              <h2 class="form-card__title">基本信息</h2>
            </div>

            <div class="form-grid">
              <div class="field span-2" data-field="title">
                <label class="field__label" for="titleInput">菜谱名称 <span class="field__req">*</span></label>
                <input class="input" id="titleInput" type="text" maxlength="40" autocomplete="off" placeholder="例如：番茄牛腩汤" />
                <span class="field__error" data-error></span>
              </div>

              <div class="field" data-field="category">
                <label class="field__label" for="categorySelect">分类 <span class="field__req">*</span></label>
                <select class="select" id="categorySelect"></select>
                <span class="field__error" data-error></span>
              </div>

              <div class="field" data-field="difficulty">
                <label class="field__label" for="difficultySelect">难度</label>
                <select class="select" id="difficultySelect"></select>
                <span class="field__error" data-error></span>
              </div>

              <div class="field" data-field="timeMinutes">
                <label class="field__label" for="timeInput">烹饪时长（分钟）</label>
                <input class="input" id="timeInput" type="number" min="1" max="600" step="1" placeholder="30" />
                <span class="field__error" data-error></span>
              </div>

              <div class="field" data-field="servings">
                <label class="field__label" for="servingsInput">份量（人份）</label>
                <input class="input" id="servingsInput" type="number" min="1" max="20" step="1" placeholder="2" />
                <span class="field__error" data-error></span>
              </div>

              <div class="field span-2" data-field="description">
                <label class="field__label" for="descInput">一句话简介</label>
                <textarea class="textarea" id="descInput" maxlength="120" rows="3" placeholder="描述一下这道菜的口感或亮点，会显示在菜谱卡片上"></textarea>
                <span class="field__hint">最多 120 字。</span>
              </div>

              <div class="field span-2" data-field="tags">
                <label class="field__label" for="tagsInput">标签</label>
                <input class="input" id="tagsInput" type="text" maxlength="60" autocomplete="off" placeholder="用逗号分隔，例如：下饭, 快手, 新手友好" />
                <span class="field__hint">标签会参与搜索，也会显示在详情页。</span>
              </div>
            </div>
          </section>

          <!-- 封面 -->
          <section class="form-card">
            <div class="form-card__head">
              <h2 class="form-card__title">封面图</h2>
              <span class="section-sub">选填，不上传时会使用图标封面</span>
            </div>

            <div class="uploader" id="coverUploader">
              <input type="file" accept="image/*" class="sr-only" aria-label="选择封面图" />
              <div class="uploader__placeholder">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M3 8a2 2 0 012-2h2.5l1.2-2h6.6L16.5 6H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2z" /><circle cx="12" cy="12.5" r="3.5" /></svg>
                <span class="uploader__title">点击或拖拽图片到此处</span>
                <span class="uploader__hint">支持 JPG / PNG / WebP，最大 8MB，会自动压缩到最长边 1200px</span>
              </div>
              <img class="uploader__preview hidden" alt="封面预览" />
              <button class="uploader__remove" type="button" aria-label="移除封面图">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" aria-hidden="true"><path d="M18 6L6 18M6 6l12 12" /></svg>
              </button>
            </div>

            <div class="emoji-picker" id="emojiPicker" role="group" aria-label="选择图标封面"></div>
          </section>

          <!-- 用料 -->
          <section class="form-card">
            <div class="field" data-field="ingredients">
              <div class="form-card__head">
                <h2 class="form-card__title">用料清单 <span class="field__req">*</span></h2>
                <button class="btn btn--ghost btn--sm" type="button" id="addIngredientBtn">+ 添加用料</button>
              </div>
              <div class="dynamic-list" id="ingredientList"></div>
              <span class="field__error" data-error></span>
            </div>
          </section>

          <!-- 步骤 -->
          <section class="form-card">
            <div class="field" data-field="steps">
              <div class="form-card__head">
                <h2 class="form-card__title">做菜步骤 <span class="field__req">*</span></h2>
                <button class="btn btn--ghost btn--sm" type="button" id="addStepBtn">+ 添加步骤</button>
              </div>
              <div class="dynamic-list" id="stepList"></div>
              <span class="field__error" data-error></span>
            </div>
          </section>

          <!-- 小贴士 -->
          <section class="form-card">
            <div class="form-card__head">
              <h2 class="form-card__title">小贴士</h2>
            </div>
            <div class="field" data-field="tips">
              <textarea class="textarea" id="tipsInput" maxlength="200" rows="3" placeholder="分享一个让这道菜更好吃的小技巧（选填）"></textarea>
            </div>
          </section>

          <div class="form-actions">
            <a class="btn btn--ghost" href="index.html" id="cancelBtn">取消</a>
            <button class="btn btn--primary" type="submit" id="saveBtn">保存菜谱</button>
          </div>
        </div>

        <!-- ============ 右侧辅助栏 ============ -->
        <aside class="form-side">
          <div class="form-card">
            <div class="form-card__head">
              <h2 class="form-card__title">填写建议</h2>
            </div>
            <ul class="hint-list">
              <li>用料写清「食材 + 用量」，例如「生抽 2 汤匙」，做菜时不用再换算。</li>
              <li>步骤尽量按实际操作顺序拆开，一步只做一件事。</li>
              <li>关键步骤（下锅、翻面、收汁）可以配一张图，之后照着做更直观。</li>
              <li>图片会自动压缩后保存在浏览器里，不会上传到任何服务器。</li>
            </ul>
          </div>

          <div class="form-card">
            <div class="form-card__head">
              <h2 class="form-card__title">本地存储</h2>
            </div>
            <p class="text-soft" id="storageText">正在读取…</p>
          </div>
        </aside>
      </form>
    </div>
  </main>

  <script src="js/data/recipes.js"></script>
  <script src="js/utils.js"></script>
  <script src="js/storage.js"></script>
  <script src="js/image.js"></script>
  <script src="js/edit.js"></script>
</body>
</html>

<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>食谱集 · 今天，做点好吃的</title>
  <meta name="description" content="一个轻量的图文菜谱平台：按菜系挑选精选菜谱、查看分步做法、记录并上传自己的菜品图片。" />
  <link rel="stylesheet" href="css/base.css" />
  <link rel="stylesheet" href="css/components.css" />
  <link rel="stylesheet" href="css/layout.css" />
</head>
<body>
  <a class="sr-only" href="#recipeGrid">跳到菜谱列表</a>

  <!-- ================= 顶部导航 ================= -->
  <header class="site-nav">
    <div class="container site-nav__inner">
      <a class="brand" href="index.html">
        <span class="brand__mark" aria-hidden="true">🍳</span>
        <span class="brand__text">
          <span class="brand__name">食谱集</span>
          <span class="brand__sub">Recipe Journal</span>
        </span>
      </a>

      <div class="site-nav__search">
        <div class="search-box search-box--sm" id="navSearchBox">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><circle cx="11" cy="11" r="7" /><path d="M20 20l-3.6-3.6" /></svg>
          <input class="input" id="navSearchInput" type="search" placeholder="搜索菜谱…" autocomplete="off" aria-label="搜索菜谱" />
          <button class="search-box__clear" type="button" data-clear="navSearchInput" aria-label="清空搜索">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" aria-hidden="true"><path d="M18 6L6 18M6 6l12 12" /></svg>
          </button>
        </div>
      </div>

      <div class="site-nav__actions">
        <a class="btn btn--primary" href="edit.html">
          <span class="btn__icon" aria-hidden="true"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round"><path d="M12 5v14M5 12h14" /></svg></span>
          新建菜谱
        </a>
      </div>
    </div>
  </header>

  <main class="page-main">
    <!-- ================= 1. 轮播图：精选菜谱 ================= -->
    <section class="home-section home-section--carousel" aria-labelledby="carouselHeading">
      <h2 class="sr-only" id="carouselHeading">精选菜谱</h2>

      <div class="container">
        <div class="carousel" id="carousel">
          <div class="carousel__progress" aria-hidden="true">
            <span class="carousel__progress-bar" id="carouselProgress"></span>
          </div>

          <div class="carousel__viewport">
            <div class="carousel__track" id="carouselTrack"></div>
          </div>

          <button class="carousel__nav carousel__nav--prev" id="carouselPrev" type="button" aria-label="上一张精选菜谱">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" focusable="false"><path d="M15 18l-6-6 6-6" /></svg>
          </button>
          <button class="carousel__nav carousel__nav--next" id="carouselNext" type="button" aria-label="下一张精选菜谱">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" focusable="false"><path d="M9 18l6-6-6-6" /></svg>
          </button>

          <button class="carousel__toggle" id="carouselToggle" type="button" aria-label="暂停自动播放" aria-pressed="false"></button>

          <div class="carousel__dots" id="carouselDots" role="group" aria-label="选择要查看的精选菜谱"></div>
        </div>
      </div>
    </section>

    <!-- ================= 2. 菜谱分类 ================= -->
    <section class="home-section" aria-labelledby="categoryHeading">
      <div class="container">
        <div class="home-section__head">
          <div class="home-section__head-left">
            <span class="home-section__dot" aria-hidden="true"></span>
            <h2 class="home-section__title" id="categoryHeading">菜谱分类</h2>
            <span class="home-section__badge" id="categoryTotal">0 个分类</span>
          </div>
          <p class="home-section__sub">按菜系与口味挑一个方向，厨房里就有谱了。</p>
        </div>

        <div class="category-grid" id="categoryGrid"></div>
      </div>
    </section>

    <!-- ================= 3. 热门菜谱 ================= -->
    <section class="home-section home-section--recipes" aria-labelledby="recipeSectionTitle">
      <div class="container">
        <div class="home-section__head">
          <div class="home-section__head-left">
            <span class="home-section__dot" aria-hidden="true"></span>
            <h2 class="home-section__title" id="recipeSectionTitle">热门菜谱</h2>
            <span class="home-section__badge" id="resultCount">共 0 道菜谱</span>
          </div>
          <button class="chip home-section__reset hidden" type="button" id="resetFilters">回到热门榜</button>
        </div>
        <p class="home-section__sub" id="recipeSectionSub">大家都在做的高人气菜谱，跟着步骤来不容易失手。</p>

        <div class="recipe-grid" id="recipeGrid"></div>

        <div class="empty-state hidden" id="emptyState">
          <div class="empty-state__art" aria-hidden="true">🍽️</div>
          <h3 class="empty-state__title">没有找到匹配的菜谱</h3>
          <p class="empty-state__text">换个关键词试试，或者清空筛选条件回到热门榜单。</p>
          <button class="btn btn--ghost" type="button" id="emptyReset">清空筛选条件</button>
        </div>
      </div>
    </section>
  </main>

  <!-- ================= 页脚 ================= -->
  <footer class="site-footer">
    <div class="container site-footer__inner">
      <div>
        <p class="site-footer__text" id="footerSummary">共 0 道菜谱，数据保存在本机浏览器中。</p>
        <p class="site-footer__text text-faint">双击 index.html 即可离线使用，无需服务器与网络。</p>
      </div>
      <div class="site-footer__actions">
        <button class="btn btn--ghost btn--sm" type="button" id="resetData">恢复初始数据</button>
        <a class="btn btn--primary btn--sm" href="edit.html">新建菜谱</a>
      </div>
    </div>
  </footer>

  <script src="js/data/recipes.js"></script>
  <script src="js/utils.js"></script>
  <script src="js/storage.js"></script>
  <script src="js/list.js"></script>
</body>
</html>
