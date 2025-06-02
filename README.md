Вот структурированная методичка для вашего проекта:

# Портал дополнительного профессионального образования

## Содержание
1. [Файл стилей (CSS)](#stylescss)
2. [PHP файлы](#php-файлы)
   - [admin.php](#adminphp)
   - [applications.php](#applicationsphp)
   - [create_application.php](#create_applicationphp)
   - [dashboard.php](#dashboardphp)
   - [index.php](#indexphp)
   - [login.php](#loginphp)
   - [logout.php](#logoutphp)
   - [register.php](#registerphp)
3. [Вспомогательные файлы](#вспомогательные-файлы)
   - [auth.php](#authphp)
   - [db.php](#dbphp)
   - [header.php](#headerphp)
   - [footer.php](#footerphp)
4. [SQL файл](#education_portalsql)

---

## styles.css {#stylescss}

```css
:root {
    --primary: #4361ee;
    --secondary: #3f37c9;
    --accent: #4895ef;
    --dark: #1b263b;
    --light: #f8f9fa;
    --success: #4cc9f0;
    --warning: #f8961e;
    --danger: #f72585;
    --gray: #6c757d;
    --light-gray: #e9ecef;
    --border-radius: 8px;
    --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    --transition: all 0.3s ease;
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
    line-height: 1.6;
    color: #333;
    background-color: #f8fafc;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

.container {
    width: 90%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
}

/* Header */
header {
    background: var(--dark);
    color: white;
    padding: 1rem 0;
    box-shadow: var(--shadow);
    position: sticky;
    top: 0;
    z-index: 1000;
}

.header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

header h1 {
    font-size: 1.8rem;
    font-weight: 700;
    color: white;
    margin: 0;
}

nav ul {
    display: flex;
    list-style: none;
    gap: 1.5rem;
}

nav ul li a {
    color: white;
    text-decoration: none;
    font-weight: 500;
    padding: 0.5rem 0;
    position: relative;
    transition: var(--transition);
}

nav ul li a:hover {
    color: var(--accent);
}

nav ul li a::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 0;
    height: 2px;
    background: var(--accent);
    transition: var(--transition);
}

nav ul li a:hover::after {
    width: 100%;
}

/* Buttons */
.btn {
    display: inline-block;
    padding: 0.75rem 1.5rem;
    background: var(--primary);
    color: white;
    border: none;
    border-radius: var(--border-radius);
    font-weight: 500;
    text-decoration: none;
    cursor: pointer;
    transition: var(--transition);
    text-align: center;
}

.btn:hover {
    background: var(--secondary);
    transform: translateY(-2px);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}

.btn-outline {
    background: transparent;
    border: 2px solid var(--primary);
    color: var(--primary);
}

.btn-outline:hover {
    background: var(--primary);
    color: white;
}

.btn-sm {
    padding: 0.5rem 1rem;
    font-size: 0.875rem;
}

/* Forms */
.form-container {
    max-width: 600px;
    margin: 2rem auto;
    background: white;
    padding: 2rem;
    border-radius: var(--border-radius);
    box-shadow: var(--shadow);
}

.form-group {
    margin-bottom: 1.5rem;
}

.form-label {
    display: block;
    margin-bottom: 0.5rem;
    font-weight: 500;
}

.form-control {
    width: 100%;
    padding: 0.75rem;
    border: 1px solid #ddd;
    border-radius: var(--border-radius);
    font-family: inherit;
    transition: var(--transition);
}

.form-control:focus {
    outline: none;
    border-color: var(--primary);
    box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.2);
}

textarea.form-control {
    min-height: 120px;
    resize: vertical;
}

/* Alerts */
.alert {
    padding: 1rem;
    margin-bottom: 1.5rem;
    border-radius: var(--border-radius);
}

.alert-success {
    background: #d1fae5;
    color: #065f46;
    border: 1px solid #a7f3d0;
}

.alert-error {
    background: #fee2e2;
    color: #b91c1c;
    border: 1px solid #fca5a5;
}

/* Tables */
.table {
    width: 100%;
    border-collapse: collapse;
    margin: 2rem 0;
    background: white;
    box-shadow: var(--shadow);
    border-radius: var(--border-radius);
    overflow: hidden;
}

.table th, .table td {
    padding: 1rem;
    text-align: left;
    border-bottom: 1px solid var(--light-gray);
}

.table th {
    background: var(--dark);
    color: white;
    font-weight: 500;
}

.table tr:hover {
    background-color: #f8f9fa;
}

/* Status badges */
.badge {
    display: inline-block;
    padding: 0.35rem 0.65rem;
    border-radius: 50rem;
    font-size: 0.875rem;
    font-weight: 500;
}

.badge-new {
    background: #dbeafe;
    color: #1d4ed8;
}

.badge-in_progress {
    background: #fef3c7;
    color: #b45309;
}

.badge-completed {
    background: #dcfce7;
    color: #15803d;
}

/* Hero section */
.hero {
    background: linear-gradient(135deg, var(--dark), var(--secondary));
    color: white;
    padding: 4rem 0;
    text-align: center;
    border-radius: var(--border-radius);
    margin: 2rem 0;
}

.hero h2 {
    font-size: 2.5rem;
    margin-bottom: 1.5rem;
}

.hero p {
    font-size: 1.25rem;
    max-width: 800px;
    margin: 0 auto 2rem;
    opacity: 0.9;
}

/* Cards */
.card {
    background: white;
    border-radius: var(--border-radius);
    overflow: hidden;
    box-shadow: var(--shadow);
    transition: var(--transition);
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
}

.card-header {
    padding: 1.5rem;
    border-bottom: 1px solid var(--light-gray);
}

.card-body {
    padding: 1.5rem;
}

.card-footer {
    padding: 1rem 1.5rem;
    border-top: 1px solid var(--light-gray);
    background: #f8f9fa;
}

/* Course cards */
.course-card {
    height: 100%;
    display: flex;
    flex-direction: column;
}

.course-img {
    height: 160px;
    background: var(--primary);
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
    font-size: 3rem;
}

.course-body {
    flex: 1;
    padding: 1.5rem;
}

.course-title {
    margin-bottom: 1rem;
    color: var(--dark);
}

.course-meta {
    display: flex;
    justify-content: space-between;
    margin-top: 1.5rem;
    color: var(--gray);
    font-size: 0.9rem;
}

/* Utility classes */
.text-center {
    text-align: center;
}

.text-gray {
    color: var(--gray);
}

.mb-2 {
    margin-bottom: 0.5rem;
}

.mb-3 {
    margin-bottom: 0.75rem;
}

.mb-4 {
    margin-bottom: 1rem;
}

.mb-5 {
    margin-bottom: 1.5rem;
}

.mt-2 {
    margin-top: 0.5rem;
}

.mt-3 {
    margin-top: 0.75rem;
}

.mt-4 {
    margin-top: 1rem;
}

.mt-5 {
    margin-top: 1.5rem;
}

.my-2 {
    margin: 0.5rem 0;
}

.my-3 {
    margin: 0.75rem 0;
}

.my-4 {
    margin: 1rem 0;
}

.my-5 {
    margin: 1.5rem 0;
}

.p-6 {
    padding: 1.5rem;
}

.flex {
    display: flex;
}

.flex-col {
    flex-direction: column;
}

.gap-2 {
    gap: 0.5rem;
}

.gap-3 {
    gap: 0.75rem;
}

.gap-4 {
    gap: 1rem;
}

.grid {
    display: grid;
}

.grid-cols-1 {
    grid-template-columns: repeat(1, minmax(0, 1fr));
}

.grid-cols-2 {
    grid-template-columns: repeat(2, minmax(0, 1fr));
}

.grid-cols-3 {
    grid-template-columns: repeat(3, minmax(0, 1fr));
}

.grid-cols-4 {
    grid-template-columns: repeat(4, minmax(0, 1fr));
}

.gap-6 {
    gap: 1.5rem;
}

/* Dashboard */
.user-dashboard {
    margin: 2rem 0;
}

.user-info {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
    margin-top: 2rem;
}

.info-card {
    background: white;
    padding: 1.5rem;
    border-radius: var(--border-radius);
    box-shadow: var(--shadow);
}

/* Footer */
footer {
    background: var(--dark);
    color: white;
    padding: 3rem 0 1.5rem;
    margin-top: auto;
}

.footer-content {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
    margin-bottom: 2rem;
}

.footer-section h3 {
    margin-bottom: 1rem;
    font-size: 1.2rem;
}

.footer-section ul {
    list-style: none;
}

.footer-section ul li {
    margin-bottom: 0.5rem;
}

.footer-section ul li a {
    color: #dee2e6;
    text-decoration: none;
    transition: var(--transition);
}

.footer-section ul li a:hover {
    color: var(--accent);
}

.copyright {
    text-align: center;
    padding-top: 1.5rem;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    color: #adb5bd;
    font-size: 0.9rem;
}

/* Responsive */
@media (max-width: 768px) {
    .header-content {
        flex-direction: column;
        gap: 1rem;
    }
    
    nav ul {
        flex-wrap: wrap;
        justify-content: center;
    }
    
    .hero h2 {
        font-size: 2rem;
    }
    
    .hero p {
        font-size: 1.1rem;
    }
    
    .grid-cols-2, .grid-cols-3, .grid-cols-4 {
        grid-template-columns: 1fr;
    }
}
```

---

## PHP файлы

### admin.php {#adminphp}

```php
<?php
require_once 'includes/auth.php';
redirectIfNotLoggedIn();
redirectIfNotAdmin();
require_once 'includes/db.php';

// Обработка изменения статуса заявки
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['status'])) {
    $application_id = $_POST['application_id'];
    $status = $_POST['status'];

    $stmt = $pdo->prepare("UPDATE applications SET status = ? WHERE id = ?");
    $stmt->execute([$status, $application_id]);
    $_SESSION['success_message'] = 'Статус заявки успешно обновлен!';
    header('Location: admin.php');
    exit();
}

// Получаем все заявки
$stmt = $pdo->query("
    SELECT a.*, u.full_name, u.login, c.name as course_name 
    FROM applications a 
    JOIN users u ON a.user_id = u.id 
    JOIN courses c ON a.course_id = c.id 
    ORDER BY a.created_at DESC
");
$applications = $stmt->fetchAll(PDO::FETCH_ASSOC);

require_once 'includes/header.php';

if (isset($_SESSION['success_message'])) {
    echo '<div class="alert alert-success container">' . htmlspecialchars($_SESSION['success_message']) . '</div>';
    unset($_SESSION['success_message']);
}
?>

<div class="container">
    <section class="my-5">
        <h2 class="mb-4">Панель администратора</h2>
        
        <?php if (empty($applications)): ?>
            <div class="card">
                <div class="card-body">
                    <p>Нет заявок</p>
                </div>
            </div>
        <?php else: ?>
            <div class="card">
                <div class="card-body">
                    <div class="table-responsive">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>Пользователь</th>
                                    <th>Логин</th>
                                    <th>Курс</th>
                                    <th>Дата начала</th>
                                    <th>Оплата</th>
                                    <th>Статус</th>
                                    <th>Дата создания</th>
                                    <th>Отзыв</th>
                                    <th>Действия</th>
                                </tr>
                            </thead>
                            <tbody>
                                <?php foreach ($applications as $app): ?>
                                    <tr>
                                        <td><?php echo htmlspecialchars($app['full_name']); ?></td>
                                        <td><?php echo htmlspecialchars($app['login']); ?></td>
                                        <td><?php echo htmlspecialchars($app['course_name']); ?></td>
                                        <td><?php echo htmlspecialchars($app['start_date']); ?></td>
                                        <td><?php echo $app['payment_method'] == 'cash' ? 'Наличные' : 'Перевод'; ?></td>
                                        <td>
                                            <span class="badge badge-<?php echo str_replace('_', '-', $app['status']); ?>">
                                                <?php 
                                                switch ($app['status']) {
                                                    case 'new': echo 'Новая'; break;
                                                    case 'in_progress': echo 'В процессе'; break;
                                                    case 'completed': echo 'Завершено'; break;
                                                    default: echo $app['status'];
                                                }
                                                ?>
                                            </span>
                                        </td>
                                        <td><?php echo htmlspecialchars($app['created_at']); ?></td>
                                        <td><?php echo !empty($app['feedback']) ? htmlspecialchars($app['feedback']) : '—'; ?></td>
                                        <td>
                                            <form method="post" class="flex gap-2">
                                                <input type="hidden" name="application_id" value="<?php echo $app['id']; ?>">
                                                <select name="status" class="form-control form-control-sm">
                                                    <option value="new" <?php echo $app['status'] == 'new' ? 'selected' : ''; ?>>Новая</option>
                                                    <option value="in_progress" <?php echo $app['status'] == 'in_progress' ? 'selected' : ''; ?>>В процессе</option>
                                                    <option value="completed" <?php echo $app['status'] == 'completed' ? 'selected' : ''; ?>>Завершено</option>
                                                </select>
                                                <button type="submit" class="btn btn-sm">Обновить</button>
                                            </form>
                                        </td>
                                    </tr>
                                <?php endforeach; ?>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        <?php endif; ?>
    </section>
</div>

<?php
require_once 'includes/footer.php';
?>
```

### applications.php {#applicationsphp}

```php
<?php
require_once 'includes/auth.php';
redirectIfNotLoggedIn();
require_once 'includes/db.php';

$user_id = $_SESSION['user_id'];

// Обработка отправки отзыва
if ($_SERVER['REQUEST_METHOD'] === 'POST' && isset($_POST['feedback'])) {
    $application_id = $_POST['application_id'];
    $feedback = trim($_POST['feedback']);

    if (!empty($feedback)) {
        $stmt = $pdo->prepare("UPDATE applications SET feedback = ? WHERE id = ? AND user_id = ?");
        $stmt->execute([$feedback, $application_id, $user_id]);
        $_SESSION['success_message'] = 'Отзыв успешно сохранен!';
        header('Location: applications.php');
        exit();
    }
}

// Получаем заявки пользователя
$stmt = $pdo->prepare("
    SELECT a.*, c.name as course_name 
    FROM applications a 
    JOIN courses c ON a.course_id = c.id 
    WHERE a.user_id = ? 
    ORDER BY a.created_at DESC
");
$stmt->execute([$user_id]);
$applications = $stmt->fetchAll(PDO::FETCH_ASSOC);

require_once 'includes/header.php';

if (isset($_SESSION['success_message'])) {
    echo '<div class="alert alert-success">' . htmlspecialchars($_SESSION['success_message']) . '</div>';
    unset($_SESSION['success_message']);
}
?>

<h2>Мои заявки</h2>

<?php if (empty($applications)): ?>
    <p>У вас пока нет заявок. <a href="create_application.php">Создать новую заявку</a></p>
<?php else: ?>
    <table>
        <thead>
            <tr>
                <th>Курс</th>
                <th>Дата начала</th>
                <th>Способ оплаты</th>
                <th>Статус</th>
                <th>Дата создания</th>
                <th>Отзыв</th>
            </tr>
        </thead>
        <tbody>
            <?php foreach ($applications as $app): ?>
                <tr>
                    <td><?php echo htmlspecialchars($app['course_name']); ?></td>
                    <td><?php echo htmlspecialchars($app['start_date']); ?></td>
                    <td><?php echo $app['payment_method'] == 'cash' ? 'Наличные' : 'Банковский перевод'; ?></td>
                    <td class="status-<?php echo str_replace('_', '-', $app['status']); ?>">
                        <?php 
                        switch ($app['status']) {
                            case 'new': echo 'Новая'; break;
                            case 'in_progress': echo 'Идет обучение'; break;
                            case 'completed': echo 'Обучение завершено'; break;
                            default: echo $app['status'];
                        }
                        ?>
                    </td>
                    <td><?php echo htmlspecialchars($app['created_at']); ?></td>
                    <td>
                        <?php if ($app['status'] == 'completed'): ?>
                            <?php if (!empty($app['feedback'])): ?>
                                <p><?php echo htmlspecialchars($app['feedback']); ?></p>
                            <?php else: ?>
                                <form method="post">
                                    <input type="hidden" name="application_id" value="<?php echo $app['id']; ?>">
                                    <textarea name="feedback" placeholder="Оставьте ваш отзыв" required></textarea>
                                    <button type="submit">Отправить отзыв</button>
                                </form>
                            <?php endif; ?>
                        <?php else: ?>
                            <p>Доступно после завершения обучения</p>
                        <?php endif; ?>
                    </td>
                </tr>
            <?php endforeach; ?>
        </tbody>
    </table>
<?php endif; ?>

<?php
require_once 'includes/footer.php';
?>
```

### create_application.php {#create_applicationphp}

```php
<?php
require_once 'includes/auth.php';
redirectIfNotLoggedIn();
require_once 'includes/db.php';

$errors = [];
$course_id = $start_date = $payment_method = '';

// Получаем список курсов
$courses = $pdo->query("SELECT * FROM courses")->fetchAll(PDO::FETCH_ASSOC);

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $course_id = $_POST['course_id'];
    $start_date = $_POST['start_date'];
    $payment_method = $_POST['payment_method'];

    // Валидация
    if (empty($course_id)) {
        $errors[] = 'Необходимо выбрать курс';
    }

    if (empty($start_date)) {
        $errors[] = 'Необходимо указать дату начала обучения';
    } elseif (strtotime($start_date) < strtotime('today')) {
        $errors[] = 'Дата начала обучения не может быть в прошлом';
    }

    if (empty($payment_method)) {
        $errors[] = 'Необходимо выбрать способ оплаты';
    }

    if (empty($errors)) {
        $stmt = $pdo->prepare("INSERT INTO applications (user_id, course_id, start_date, payment_method) VALUES (?, ?, ?, ?)");
        $stmt->execute([$_SESSION['user_id'], $course_id, $start_date, $payment_method]);

        $_SESSION['success_message'] = 'Заявка успешно создана!';
        header('Location: applications.php');
        exit();
    }
}

require_once 'includes/header.php';
?>

<h2>Создание новой заявки</h2>

<?php if (!empty($errors)): ?>
    <div class="alert alert-error">
        <ul>
            <?php foreach ($errors as $error): ?>
                <li><?php echo htmlspecialchars($error); ?></li>
            <?php endforeach; ?>
        </ul>
    </div>
<?php endif; ?>

<form method="post">
    <div>
        <label for="course_id">Курс:</label>
        <select id="course_id" name="course_id" required>
            <option value="">-- Выберите курс --</option>
            <?php foreach ($courses as $course): ?>
                <option value="<?php echo $course['id']; ?>" <?php echo ($course_id == $course['id']) ? 'selected' : ''; ?>>
                    <?php echo htmlspecialchars($course['name']); ?>
                </option>
            <?php endforeach; ?>
        </select>
    </div>
    <div>
        <label for="start_date">Желаемая дата начала обучения:</label>
        <input type="date" id="start_date" name="start_date" value="<?php echo htmlspecialchars($start_date); ?>" required>
    </div>
    <div>
        <label>Способ оплаты:</label>
        <div>
            <input type="radio" id="cash" name="payment_method" value="cash" <?php echo ($payment_method == 'cash') ? 'checked' : ''; ?> required>
            <label for="cash">Наличные</label>
        </div>
        <div>
            <input type="radio" id="bank_transfer" name="payment_method" value="bank_transfer" <?php echo ($payment_method == 'bank_transfer') ? 'checked' : ''; ?> required>
            <label for="bank_transfer">Перевод на банковский счет</label>
        </div>
    </div>
    <div>
        <button type="submit">Отправить заявку</button>
    </div>
</form>

<?php
require_once 'includes/footer.php';
?>
```

### dashboard.php {#dashboardphp}

```php
<?php
require_once 'includes/auth.php';
redirectIfNotLoggedIn();

require_once 'includes/db.php';
require_once 'includes/header.php';

$user_id = $_SESSION['user_id'];
$stmt = $pdo->prepare("SELECT full_name, email, phone FROM users WHERE id = ?");
$stmt->execute([$user_id]);
$user = $stmt->fetch();
?>

<div class="container">
    <section class="user-dashboard">
        <h2>Добро пожаловать, <?php echo htmlspecialchars($user['full_name']); ?>!</h2>
        <p class="text-gray">Ваш персональный кабинет для управления обучением</p>
        
        <div class="user-info">
            <div class="info-card">
                <h3 class="mb-4">Ваш профиль</h3>
                <div class="mb-3">
                    <p class="text-sm text-gray">Email</p>
                    <p><?php echo htmlspecialchars($user['email']); ?></p>
                </div>
                <div class="mb-3">
                    <p class="text-sm text-gray">Телефон</p>
                    <p><?php echo htmlspecialchars($user['phone']); ?></p>
                </div>
                <div>
                    <p class="text-sm text-gray">Логин</p>
                    <p><?php echo htmlspecialchars($_SESSION['login']); ?></p>
                </div>
            </div>
            
            <div class="info-card">
                <h3 class="mb-4">Быстрые действия</h3>
                <div class="flex flex-col gap-3">
                    <a href="create_application.php" class="btn">Подать новую заявку</a>
                    <a href="applications.php" class="btn btn-outline">Мои заявки</a>
                    <?php if (isAdmin()): ?>
                        <a href="admin.php" class="btn btn-outline">Панель администратора</a>
                    <?php endif; ?>
                </div>
            </div>
        </div>
    </section>
</div>

<?php
require_once 'includes/footer.php';
?>
```

### index.php {#indexphp}

```php
<?php
require_once 'includes/auth.php';
require_once 'includes/header.php';
?>

<section class="hero">
    <div class="container">
        <h2>Профессиональное обучение для карьерного роста</h2>
        <p>Получите актуальные знания и навыки от практикующих экспертов. Станьте востребованным специалистом с нашими образовательными программами.</p>
        
        <?php if (!isLoggedIn()): ?>
            <div class="mt-4">
                <a href="register.php" class="btn">Начать обучение</a>
                <a href="login.php" class="btn btn-outline ml-2">Войти</a>
            </div>
        <?php endif; ?>
    </div>
</section>

<div class="container">
    <section class="my-5">
        <h2 class="text-center mb-4">Наши программы обучения</h2>
        <p class="text-center text-gray mb-5">Выберите направление, которое соответствует вашим профессиональным целям</p>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            <div class="course-card">
                <div class="course-img">🐍</div>
                <div class="course-body">
                    <h3 class="course-title">Python для профессионалов</h3>
                    <p class="text-gray">Глубокое погружение в Python: от основ до продвинутых концепций и фреймворков.</p>
                    <div class="course-meta">
                        <span>3 месяца</span>
                        <span>15 000 ₽</span>
                    </div>
                </div>
            </div>
            
            <div class="course-card">
                <div class="course-img">🌐</div>
                <div class="course-body">
                    <h3 class="course-title">Современная веб-разработка</h3>
                    <p class="text-gray">Полный цикл создания веб-приложений с использованием современных технологий.</p>
                    <div class="course-meta">
                        <span>4 месяца</span>
                        <span>20 000 ₽</span>
                    </div>
                </div>
            </div>
            
            <div class="course-card">
                <div class="course-img">📊</div>
                <div class="course-body">
                    <h3 class="course-title">Анализ данных</h3>
                    <p class="text-gray">Методы анализа данных, визуализация и основы машинного обучения.</p>
                    <div class="course-meta">
                        <span>2.5 месяца</span>
                        <span>18 000 ₽</span>
                    </div>
                </div>
            </div>
            
            <div class="course-card">
                <div class="course-img">🎨</div>
                <div class="course-body">
                    <h3 class="course-title">Дизайн интерфейсов</h3>
                    <p class="text-gray">Создание удобных и эстетичных интерфейсов с учетом UX/UI принципов.</p>
                    <div class="course-meta">
                        <span>2 месяца</span>
                        <span>12 000 ₽</span>
                    </div>
                </div>
            </div>
            
            <div class="course-card">
                <div class="course-img">📢</div>
                <div class="course-body">
                    <h3 class="course-title">Digital-маркетинг</h3>
                    <p class="text-gray">Стратегии продвижения в цифровой среде и работа с рекламными инструментами.</p>
                    <div class="course-meta">
                        <span>3 месяца</span>
                        <span>16 000 ₽</span>
                    </div>
                </div>
            </div>
            
            <div class="course-card">
                <div class="course-img">🤖</div>
                <div class="course-body">
                    <h3 class="course-title">Машинное обучение</h3>
                    <p class="text-gray">Основы искусственного интеллекта и практическое применение алгоритмов.</p>
                    <div class="course-meta">
                        <span>3.5 месяца</span>
                        <span>22 000 ₽</span>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <section class="my-5 py-5">
        <h2 class="text-center mb-4">Наши преимущества</h2>
        <p class="text-center text-gray mb-5">Почему студенты выбирают нашу платформу для профессионального развития</p>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
            <div class="card text-center p-6">
                <div class="text-4xl mb-4">👨‍🏫</div>
                <h3 class="mb-2">Эксперты-практики</h3>
                <p class="text-gray">Преподаватели с опытом работы в ведущих компаниях отрасли</p>
            </div>
            
            <div class="card text-center p-6">
                <div class="text-4xl mb-4">⏱️</div>
                <h3 class="mb-2">Гибкий график</h3>
                <p class="text-gray">Возможность совмещать обучение с работой и личными делами</p>
            </div>
            
            <div class="card text-center p-6">
                <div class="text-4xl mb-4">📜</div>
                <h3 class="mb-2">Сертификат</h3>
                <p class="text-gray">Документ об окончании, подтверждающий ваши компетенции</p>
            </div>
            
            <div class="card text-center p-6">
                <div class="text-4xl mb-4">💼</div>
                <h3 class="mb-2">Карьера</h3>
                <p class="text-gray">Помощь в трудоустройстве и развитии карьеры</p>
            </div>
        </div>
    </section>
</div>

<?php
require_once 'includes/footer.php';
?>
```

### login.php {#loginphp}

```php
<?php
require_once 'includes/db.php';
require_once 'includes/auth.php';

if (isLoggedIn()) {
    header('Location: dashboard.php');
    exit();
}

$errors = [];
$login = '';

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $login = trim($_POST['login']);
    $password = $_POST['password'];

    if (empty($login) || empty($password)) {
        $errors[] = 'Логин и пароль обязательны для заполнения';
    } else {
        $stmt = $pdo->prepare("SELECT * FROM users WHERE login = ?");
        $stmt->execute([$login]);
        $user = $stmt->fetch();

        if ($user && $password === $user['password']) {
            $_SESSION['user_id'] = $user['id'];
            $_SESSION['login'] = $user['login'];
            $_SESSION['is_admin'] = ($user['login'] === 'admin');
            
            header('Location: dashboard.php');
            exit();
        } else {
            $errors[] = 'Неверный логин или пароль';
        }
    }
}

require_once 'includes/header.php';

if (isset($_SESSION['success_message'])) {
    echo '<div class="alert alert-success">' . htmlspecialchars($_SESSION['success_message']) . '</div>';
    unset($_SESSION['success_message']);
}
?>

<div class="form-container">
    <h2 class="text-center mb-4">Вход в систему</h2>
    
    <?php if (!empty($errors)): ?>
        <div class="alert alert-error">
            <ul>
                <?php foreach ($errors as $error): ?>
                    <li><?php echo htmlspecialchars($error); ?></li>
                <?php endforeach; ?>
            </ul>
        </div>
    <?php endif; ?>

    <form method="post">
        <div class="form-group">
            <label for="login" class="form-label">Логин:</label>
            <input type="text" id="login" name="login" class="form-control" value="<?php echo htmlspecialchars($login); ?>" required>
        </div>
        
        <div class="form-group">
            <label for="password" class="form-label">Пароль:</label>
            <input type="password" id="password" name="password" class="form-control" required>
        </div>
        
        <div class="form-group">
            <button type="submit" class="btn w-full">Войти</button>
        </div>
    </form>

    <p class="text-center mt-4">Еще не зарегистрированы? <a href
Вот остальные файлы вашего проекта, оформленные в том же стиле методички:

---

## Вспомогательные файлы

### auth.php {#authphp}

```php
<?php
session_start();

function isLoggedIn() {
    return isset($_SESSION['user_id']);
}

function isAdmin() {
    return isset($_SESSION['is_admin']) && $_SESSION['is_admin'];
}

function redirectIfNotLoggedIn() {
    if (!isLoggedIn()) {
        header('Location: login.php');
        exit();
    }
}

function redirectIfNotAdmin() {
    if (!isAdmin()) {
        header('Location: dashboard.php');
        exit();
    }
}
?>
```

### db.php {#dbphp}

```php
<?php
$host = 'localhost';
$dbname = 'education_portal';
$username = 'root';
$password = '';

try {
    $pdo = new PDO("mysql:host=$host;dbname=$dbname;charset=utf8", $username, $password);
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
    die("Ошибка подключения к базе данных: " . $e->getMessage());
}
?>
```

### header.php {#headerphp}

```php
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Портал ДПО</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <header>
        <div class="container">
            <h1>Корочки.есть</h1>
            <nav>
                <ul>
                    <?php if (isLoggedIn()): ?>
                        <li><a href="dashboard.php">Главная</a></li>
                        <li><a href="create_application.php">Новая заявка</a></li>
                        <li><a href="applications.php">Мои заявки</a></li>
                        <?php if (isAdmin()): ?>
                            <li><a href="admin.php">Панель администратора</a></li>
                        <?php endif; ?>
                        <li><a href="logout.php">Выйти</a></li>
                    <?php else: ?>
                        <li><a href="index.php">Главная</a></li>
                        <li><a href="register.php">Регистрация</a></li>
                        <li><a href="login.php">Вход</a></li>
                    <?php endif; ?>
                </ul>
            </nav>
        </div>
    </header>
    <main class="container">
```

### footer.php {#footerphp}

```php
    </main>
    <footer>
        <div class="container">
            <p>&copy; <?php echo date('Y'); ?> Портал дополнительного профессионального образования</p>
        </div>
    </footer>
</body>
</html>
```

### logout.php {#logoutphp}

```php
<?php
require_once 'includes/auth.php';

session_destroy();
header('Location: login.php');
exit();
?>
```

---

## education_portal.sql {#education_portalsql}

```sql
CREATE DATABASE education_portal;

USE education_portal;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    full_name VARCHAR(100) NOT NULL,
    phone VARCHAR(20) NOT NULL,
    email VARCHAR(50) NOT NULL,
    login VARCHAR(30) NOT NULL UNIQUE,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE courses (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);

CREATE TABLE applications (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    course_id INT NOT NULL,
    start_date DATE NOT NULL,
    payment_method ENUM('cash', 'bank_transfer') NOT NULL,
    status ENUM('new', 'in_progress', 'completed') DEFAULT 'new',
    feedback TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (course_id) REFERENCES courses(id)
);

-- Добавим несколько курсов
INSERT INTO courses (name) VALUES 
('Программирование на Python'),
('Веб-разработка'),
('Анализ данных'),
('Графический дизайн'),
('Маркетинг и реклама');

-- Администратор
INSERT INTO users (full_name, phone, email, login, password) VALUES 
('Администратор', '+7(999)-999-99-99', 'admin@edu.ru', 'admin', '$2y$10$92IXUNpkjO0rOQ5byMi.Ye4oKoEa3Ro9llC/.og/at2.uheWG/igi');
-- Пароль: education

UPDATE users SET password = 'education' WHERE login = 'admin';
```

---

## Структура проекта

```
education_portal/
│
├── css/
│   └── style.css
│
├── includes/
│   ├── auth.php
│   ├── db.php
│   ├── header.php
│   └── footer.php
│
├── admin.php
├── applications.php
├── create_application.php
├── dashboard.php
├── index.php
├── login.php
├── logout.php
├── register.php
│
└── education_portal.sql
```


### register.php {#registerphp}

```php
<?php
require_once 'includes/db.php';
require_once 'includes/auth.php';

if (isLoggedIn()) {
    header('Location: dashboard.php');
    exit();
}

$errors = [];
$full_name = $phone = $email = $login = $password = '';

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $full_name = trim($_POST['full_name']);
    $phone = trim($_POST['phone']);
    $email = trim($_POST['email']);
    $login = trim($_POST['login']);
    $password = $_POST['password'];

    // Валидация
    if (empty($full_name)) {
        $errors[] = 'ФИО обязательно для заполнения';
    } elseif (!preg_match('/^[А-Яа-яЁё\s]+$/u', $full_name)) {
        $errors[] = 'ФИО должно содержать только кириллические символы и пробелы';
    }

    if (empty($phone)) {
        $errors[] = 'Телефон обязателен для заполнения';
    } elseif (!preg_match('/^\+7\(\d{3}\)-\d{3}-\d{2}-\d{2}$/', $phone)) {
        $errors[] = 'Телефон должен быть в формате +7(XXX)-XXX-XX-XX';
    }

    if (empty($email)) {
        $errors[] = 'Email обязателен для заполнения';
    } elseif (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
        $errors[] = 'Некорректный формат email';
    }

    if (empty($login)) {
        $errors[] = 'Логин обязателен для заполнения';
    } elseif (strlen($login) < 6) {
        $errors[] = 'Логин должен содержать не менее 6 символов';
    } elseif (!preg_match('/^[А-Яа-яЁё0-9_]+$/u', $login)) {
        $errors[] = 'Логин должен содержать только кириллические символы, цифры и подчеркивания';
    }

    if (empty($password)) {
        $errors[] = 'Пароль обязателен для заполнения';
    } elseif (strlen($password) < 6) {
        $errors[] = 'Пароль должен содержать не менее 6 символов';
    }

    // Проверка уникальности логина
    if (empty($errors)) {
        $stmt = $pdo->prepare("SELECT id FROM users WHERE login = ?");
        $stmt->execute([$login]);
        if ($stmt->fetch()) {
            $errors[] = 'Этот логин уже занят';
        }
    }

    if (empty($errors)) {
        $hashed_password = password_hash($password, PASSWORD_DEFAULT);
        $stmt = $pdo->prepare("INSERT INTO users (full_name, phone, email, login, password) VALUES (?, ?, ?, ?, ?)");
        $stmt->execute([$full_name, $phone, $email, $login, $hashed_password]);

        $_SESSION['success_message'] = 'Регистрация прошла успешно! Теперь вы можете войти.';
        header('Location: login.php');
        exit();
    }
}

require_once 'includes/header.php';
?>

<div class="form-container">
    <h2 class="text-center mb-4">Регистрация</h2>
    
    <?php if (!empty($errors)): ?>
        <div class="alert alert-error">
            <ul>
                <?php foreach ($errors as $error): ?>
                    <li><?php echo htmlspecialchars($error); ?></li>
                <?php endforeach; ?>
            </ul>
        </div>
    <?php endif; ?>

    <form method="post">
        <div class="form-group">
            <label for="full_name" class="form-label">ФИО:</label>
            <input type="text" id="full_name" name="full_name" class="form-control" 
                   value="<?php echo htmlspecialchars($full_name); ?>" required>
        </div>
        
        <div class="form-group">
            <label for="phone" class="form-label">Телефон:</label>
            <input type="text" id="phone" name="phone" class="form-control" 
                   placeholder="+7(XXX)-XXX-XX-XX" value="<?php echo htmlspecialchars($phone); ?>" required>
        </div>
        
        <div class="form-group">
            <label for="email" class="form-label">Email:</label>
            <input type="email" id="email" name="email" class="form-control" 
                   value="<?php echo htmlspecialchars($email); ?>" required>
        </div>
        
        <div class="form-group">
            <label for="login" class="form-label">Логин:</label>
            <input type="text" id="login" name="login" class="form-control" 
                   value="<?php echo htmlspecialchars($login); ?>" required>
            <small class="text-gray">Не менее 6 символов (кириллица, цифры, _)</small>
        </div>
        
        <div class="form-group">
            <label for="password" class="form-label">Пароль:</label>
            <input type="password" id="password" name="password" class="form-control" required>
            <small class="text-gray">Не менее 6 символов</small>
        </div>
        
        <div class="form-group">
            <button type="submit" class="btn w-full">Зарегистрироваться</button>
        </div>
    </form>

    <p class="text-center mt-4">Уже есть аккаунт? <a href="login.php" class="text-primary">Войти</a></p>
</div>

<?php
require_once 'includes/footer.php';
?>
