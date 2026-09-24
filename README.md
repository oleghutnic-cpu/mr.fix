# mr.fix
site
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mr. Fix — умный помощник: герметик, клей, крепёж</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
    <script src="https://elfsightcdn.com/platform.js" async></script>
    <style>
        :root {
            --primary: #CC0000; --primary-dark: #990000; --primary-light: #FFE5E5;
            --secondary: #FFCC00; --secondary-light: #FFF8E1;
            --success: #22A65E; --danger: #D92B2B; --warning: #F59E0B;
            --white: #FFFFFF; --gray-50: #F8F9FA; --gray-100: #F1F2F4;
            --gray-200: #E4E5E7; --gray-300: #C4C6C9; --gray-400: #A3A6AB;
            --gray-500: #808388; --gray-600: #666A70; --gray-700: #4D5158;
            --gray-800: #33373E; --gray-900: #1A1E24;
            --radius-sm: 4px; --radius-md: 8px; --radius-lg: 12px; --radius-xl: 16px;
            --shadow-sm: 0 1px 3px rgba(0,0,0,0.12);
            --shadow-md: 0 4px 20px rgba(0,0,0,0.15);
            --shadow-lg: 0 8px 40px rgba(0,0,0,0.2);
            --shadow-xl: 0 20px 60px rgba(0,0,0,0.25);
            --transition-base: 0.25s cubic-bezier(0.4, 0, 0.2, 1);
            --font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        }
        * { margin: 0; padding: 0; box-sizing: border-box; }
        html { scroll-behavior: smooth; }
        body { font-family: var(--font-family); background: var(--gray-50); color: var(--gray-900); line-height: 1.6; -webkit-font-smoothing: antialiased; }
        .container { max-width: 1400px; margin: 0 auto; padding: 0 24px; }

        .btn { display: inline-flex; align-items: center; justify-content: center; gap: 8px; padding: 10px 24px; border-radius: 40px; font-weight: 600; font-size: 14px; border: none; cursor: pointer; transition: var(--transition-base); text-decoration: none; text-align: center; }
        .btn-primary { background: var(--primary); color: var(--white); }
        .btn-primary:hover { background: var(--primary-dark); transform: translateY(-2px); box-shadow: 0 8px 30px rgba(204,0,0,0.35); }
        .btn-secondary { background: var(--secondary); color: var(--gray-900); }
        .btn-secondary:hover { background: #E6B800; transform: translateY(-2px); }
        .btn-outline { background: transparent; border: 2px solid var(--primary); color: var(--primary); }
        .btn-outline:hover { background: var(--primary); color: var(--white); }
        .btn-sm { padding: 6px 16px; font-size: 12px; }

        .header { position: fixed; top: 0; left: 0; right: 0; z-index: 1000; background: rgba(255,255,255,0.97); backdrop-filter: blur(12px); border-bottom: 1px solid var(--gray-200); padding: 6px 0; transition: var(--transition-base); }
        .header.scrolled { box-shadow: var(--shadow-md); }
        .header .container { display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 10px; }
        .logo { display: flex; align-items: center; gap: 10px; text-decoration: none; }
        .logo-mark { width: 44px; height: 44px; background: var(--primary); border-radius: 10px; display: flex; align-items: center; justify-content: center; flex-shrink: 0; position: relative; overflow: hidden; }
        .logo-mark::after { content: ''; position: absolute; bottom: 0; left: 0; right: 0; height: 8px; background: var(--secondary); }
        .logo-mark svg { width: 100%; height: 100%; }
        .logo-text { font-size: 22px; font-weight: 900; letter-spacing: -0.02em; display: flex; align-items: center; gap: 2px; color: var(--gray-900); line-height: 1; }
        .logo-text .mr { color: var(--primary); font-size: 14px; font-weight: 800; letter-spacing: 0.05em; align-self: flex-start; margin-top: 2px; }
        .logo-text .fix { color: var(--gray-900); }
        .logo-sub { font-size: 9px; color: var(--gray-500); letter-spacing: 0.1em; text-transform: uppercase; font-weight: 500; }
        .nav { display: flex; gap: 20px; align-items: center; flex-wrap: wrap; }
        .nav a { font-weight: 500; font-size: 13px; padding: 4px 0; color: var(--gray-600); border-bottom: 2px solid transparent; text-decoration: none; transition: var(--transition-base); }
        .nav a:hover, .nav a.active { color: var(--gray-900); border-bottom-color: var(--primary); }
        .header-actions { display: flex; align-items: center; gap: 12px; }
        .header-actions .phone { font-weight: 600; font-size: 13px; color: var(--gray-700); white-space: nowrap; text-decoration: none; }
        .header-actions .phone:hover { color: var(--primary); }
        .cart-btn { position: relative; background: var(--gray-100); border: 1px solid var(--gray-200); border-radius: 50%; width: 42px; height: 42px; display: flex; align-items: center; justify-content: center; cursor: pointer; color: var(--gray-700); text-decoration: none; transition: var(--transition-base); }
        .cart-btn:hover { border-color: var(--primary); color: var(--primary); background: var(--primary-light); }
        .cart-count { position: absolute; top: -5px; right: -5px; background: var(--primary); color: var(--white); font-size: 10px; font-weight: 800; width: 20px; height: 20px; border-radius: 50%; display: none; align-items: center; justify-content: center; border: 2px solid var(--white); }
        .burger { display: none; background: none; border: 0; font-size: 24px; cursor: pointer; color: var(--gray-900); padding: 4px 8px; }

        .hero { padding: 100px 0 50px; background: linear-gradient(165deg, #FFF5F5 0%, #FFFFFF 60%, #FFFDE8 100%); position: relative; overflow: hidden; }
        .hero::before { content: ''; position: absolute; top: -40%; right: -10%; width: 600px; height: 600px; background: radial-gradient(circle, rgba(204,0,0,0.04) 0%, transparent 70%); border-radius: 50%; }
        .hero-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: center; position: relative; z-index: 1; }
        .hero-badge { display: inline-block; font-weight: 600; font-size: 11px; letter-spacing: 0.15em; text-transform: uppercase; color: var(--primary); background: var(--primary-light); padding: 4px 16px; border-radius: 20px; margin-bottom: 10px; }
        .hero h1 { font-size: 38px; font-weight: 900; line-height: 1.05; margin: 14px 0 18px; letter-spacing: -0.03em; color: var(--gray-900); }
        .hero h1 .highlight { background: linear-gradient(135deg, var(--primary), var(--secondary)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
        .hero-quote { font-size: 15px; font-style: italic; color: var(--gray-600); border-left: 3px solid var(--secondary); padding-left: 14px; margin: 18px 0 20px; line-height: 1.6; }
        .hero-desc { font-size: 16px; color: var(--gray-600); max-width: 480px; margin-bottom: 24px; line-height: 1.7; }
        .hero-actions { display: flex; gap: 12px; flex-wrap: wrap; }
        .hero-stats { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .stat-item { background: var(--white); border: 1px solid var(--gray-200); border-radius: var(--radius-md); padding: 18px 16px; text-align: center; transition: var(--transition-base); box-shadow: var(--shadow-sm); }
        .stat-item:hover { border-color: var(--primary); box-shadow: var(--shadow-md); transform: translateY(-2px); }
        .stat-number { font-size: 28px; font-weight: 800; color: var(--primary); display: block; letter-spacing: -0.02em; }
        .stat-label { font-size: 13px; color: var(--gray-500); font-weight: 500; }

        .search-section { background: var(--white); padding: 30px 0 40px; border-bottom: 1px solid var(--gray-200); }
        .search-section h2 { text-align: center; font-size: 26px; font-weight: 700; margin-bottom: 6px; color: var(--gray-900); }
        .search-section .sub { text-align: center; color: var(--gray-500); margin-bottom: 24px; font-size: 15px; }
        .smart-search { max-width: 820px; margin: 0 auto; }
        .search-container { display: flex; gap: 12px; margin-bottom: 20px; }
        .search-container input { flex: 1; padding: 14px 20px; border: 2px solid var(--gray-300); border-radius: var(--radius-md); font-size: 15px; transition: var(--transition-base); font-family: inherit; background: var(--white); color: var(--gray-900); }
        .search-container input::placeholder { color: var(--gray-500); }
        .search-container input:focus { outline: none; border-color: var(--primary); box-shadow: 0 0 0 4px rgba(204,0,0,0.08); }
        .search-tags { display: flex; gap: 10px; flex-wrap: wrap; justify-content: center; }
        .tag { padding: 6px 18px; border: 1px solid var(--gray-300); border-radius: 30px; font-size: 12px; cursor: pointer; transition: var(--transition-base); color: var(--gray-600); text-decoration: none; background: var(--white); }
        .tag:hover { border-color: var(--primary); color: var(--primary); background: var(--primary-light); }

        .section { padding: 40px 0; }
        .section-title { font-size: 28px; font-weight: 800; text-align: center; margin-bottom: 6px; letter-spacing: -0.02em; color: var(--gray-900); }
        .section-sub { text-align: center; font-size: 15px; color: var(--gray-500); margin-bottom: 28px; }
        .section-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; flex-wrap: wrap; gap: 12px; }
        .section-header h2 { font-size: 22px; font-weight: 800; letter-spacing: -0.02em; color: var(--gray-900); }

        .tasks-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
        .task-card { background: var(--white); border: 1px solid var(--gray-200); border-radius: var(--radius-md); padding: 22px 18px; text-align: center; transition: var(--transition-base); }
        .task-card:hover { border-color: var(--primary); transform: translateY(-4px); box-shadow: var(--shadow-md); }
        .task-icon { font-size: 36px; display: block; margin-bottom: 8px; }
        .task-card h3 { font-size: 16px; font-weight: 700; margin-bottom: 4px; color: var(--gray-900); }
        .task-card p { font-size: 13px; color: var(--gray-500); margin-bottom: 12px; }

        .benefits-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 18px; }
        .benefit-card { background: var(--white); border: 1px solid var(--gray-200); border-radius: var(--radius-md); padding: 22px 18px; text-align: center; transition: var(--transition-base); }
        .benefit-card:hover { border-color: var(--primary); transform: translateY(-4px); box-shadow: var(--shadow-md); }
        .benefit-icon { font-size: 32px; display: block; margin-bottom: 10px; }
        .benefit-card h3 { font-size: 15px; font-weight: 700; margin-bottom: 4px; color: var(--gray-900); }
        .benefit-card p { font-size: 13px; color: var(--gray-500); }

        .catalog-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 18px; }
        .product-card { background: var(--white); border: 1px solid var(--gray-200); border-radius: var(--radius-md); padding: 14px; transition: var(--transition-base); display: flex; flex-direction: column; position: relative; }
        .product-card:hover { transform: translateY(-4px); border-color: var(--primary); box-shadow: var(--shadow-lg); }
        .product-card__image { width: 100%; aspect-ratio: 1/1; background: var(--gray-100); border-radius: var(--radius-sm); overflow: hidden; margin-bottom: 10px; display: flex; align-items: center; justify-content: center; position: relative; }
        .product-card__image img { width: 100%; height: 100%; object-fit: contain; transition: var(--transition-base); padding: 8px; }
        .product-card:hover .product-card__image img { transform: scale(1.04); }
        .product-card__badge { position: absolute; top: 6px; right: 6px; background: var(--secondary); color: var(--gray-900); font-size: 9px; font-weight: 800; text-transform: uppercase; padding: 2px 10px; border-radius: 20px; letter-spacing: 0.04em; z-index: 2; }
        .product-card__sku { font-size: 10px; color: var(--gray-500); font-family: monospace; margin-bottom: 2px; }
        .product-card__title { font-size: 13px; font-weight: 600; margin: 0 0 2px; line-height: 1.3; color: var(--gray-900); display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical; overflow: hidden; }
        .product-card__rating { display: flex; align-items: center; gap: 6px; margin: 4px 0 6px; }
        .product-card__stars { color: var(--secondary); font-size: 12px; letter-spacing: 1px; }
        .product-card__reviews { font-size: 11px; color: var(--gray-500); }
        .product-card__price { display: flex; align-items: baseline; flex-wrap: wrap; gap: 6px; margin: 4px 0 8px; padding-top: 6px; border-top: 1px solid var(--gray-200); }
        .product-card__price-current { font-size: 17px; font-weight: 800; color: var(--gray-900); }
        .product-card__price-wholesale { font-size: 11px; font-weight: 600; color: var(--primary); background: var(--primary-light); padding: 2px 8px; border-radius: 12px; }
        .product-card__stock { font-size: 11px; font-weight: 600; margin: 0 0 8px; }
        .product-card__stock--in { color: var(--success); }
        .product-card__stock--order { color: var(--warning); }
        .product-card__actions { display: flex; gap: 6px; flex-wrap: wrap; margin-top: auto; }
        .product-card__actions .btn { flex: 1; min-width: 44px; padding: 6px 10px; font-size: 11px; }
        .product-card__actions .btn--tech { flex: 0.5; background: var(--gray-100); color: var(--gray-600); border: 1px solid var(--gray-300); }
        .product-card__actions .btn--tech:hover { background: var(--gray-200); color: var(--gray-900); }

        .price-section { padding: 40px 0; background: var(--white); }
        .price-section .section-header { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 12px; margin-bottom: 20px; }
        .price-section .section-header h2 { font-size: 24px; font-weight: 800; color: var(--gray-900); display: flex; align-items: center; gap: 10px; }
        .price-section .section-header .badge { font-size: 12px; font-weight: 600; background: var(--primary); color: var(--white); padding: 2px 12px; border-radius: 20px; }
        .price-toolbar { display: flex; flex-wrap: wrap; gap: 10px; align-items: center; margin-bottom: 16px; padding: 12px 16px; background: var(--gray-50); border-radius: var(--radius-md); border: 1px solid var(--gray-200); }
        .price-toolbar input { flex: 1; min-width: 160px; padding: 8px 14px; border: 1px solid var(--gray-300); border-radius: var(--radius-md); background: var(--white); color: var(--gray-900); font-size: 13px; font-family: inherit; }
        .price-toolbar input:focus { outline: none; border-color: var(--primary); }
        .price-toolbar select { padding: 8px 14px; border: 1px solid var(--gray-300); border-radius: var(--radius-md); background: var(--white); color: var(--gray-900); font-size: 13px; font-family: inherit; cursor: pointer; }
        .price-toolbar select:focus { outline: none; border-color: var(--primary); }
        .price-toolbar .count { font-size: 13px; color: var(--gray-500); margin-left: auto; }
        .price-accordion { border-radius: var(--radius-md); border: 1px solid var(--gray-200); overflow: hidden; }
        .price-category { border-bottom: 1px solid var(--gray-200); }
        .price-category:last-child { border-bottom: none; }
        .price-category-header { display: flex; justify-content: space-between; align-items: center; padding: 12px 18px; background: var(--gray-50); cursor: pointer; transition: var(--transition-base); user-select: none; }
        .price-category-header:hover { background: var(--gray-100); }
        .price-category-header .cat-title { font-weight: 600; color: var(--gray-900); font-size: 14px; display: flex; align-items: center; gap: 10px; }
        .price-category-header .cat-count { font-size: 11px; color: var(--gray-500); background: var(--gray-200); padding: 2px 10px; border-radius: 12px; }
        .price-category-header .arrow { color: var(--gray-500); transition: var(--transition-base); font-size: 14px; }
        .price-category-header.open .arrow { transform: rotate(180deg); }
        .price-category-body { display: none; overflow-x: auto; }
        .price-category-body.open { display: block; }
        .price-table { width: 100%; border-collapse: collapse; font-size: 12px; min-width: 650px; }
        .price-table thead { background: var(--gray-100); }
        .price-table th { padding: 8px 12px; text-align: left; font-weight: 600; color: var(--gray-600); font-size: 10px; text-transform: uppercase; letter-spacing: 0.05em; white-space: nowrap; position: sticky; top: 0; background: var(--gray-100); z-index: 1; }
        .price-table td { padding: 6px 12px; border-bottom: 1px solid var(--gray-200); color: var(--gray-700); vertical-align: middle; }
        .price-table tr:hover td { background: rgba(204,0,0,0.02); }
        .price-table .product-cell .name { font-weight: 500; color: var(--gray-900); font-size: 12px; }
        .price-table .product-cell .sku { font-size: 10px; color: var(--gray-500); font-family: monospace; }
        .price-table .brand-tag { font-size: 10px; font-weight: 600; padding: 2px 8px; border-radius: 12px; background: var(--gray-100); color: var(--gray-600); }
        .price-table .price-current { font-weight: 700; color: var(--gray-900); }
        .price-table .price-wholesale { color: var(--primary); font-weight: 600; }
        .price-table .stock-in { color: var(--success); }
        .price-table .stock-order { color: var(--warning); }

        .payment-section { padding: 40px 0; background: var(--gray-50); border-top: 1px solid var(--gray-200); }
        .payment-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; max-width: 1100px; margin: 0 auto; }
        .payment-card { background: var(--white); border: 1px solid var(--gray-200); border-radius: var(--radius-md); padding: 24px; text-align: center; transition: var(--transition-base); }
        .payment-card:hover { border-color: var(--primary); transform: translateY(-4px); box-shadow: var(--shadow-md); }
        .payment-card .icon { font-size: 36px; display: block; margin-bottom: 12px; }
        .payment-card h3 { font-size: 16px; font-weight: 700; margin-bottom: 8px; color: var(--gray-900); }
        .payment-card p { font-size: 13px; color: var(--gray-500); line-height: 1.6; }

        .documents-section { padding: 40px 0; background: var(--white); }
        .doc-tabs { display: flex; justify-content: center; gap: 10px; margin-bottom: 24px; flex-wrap: wrap; }
        .doc-tab { padding: 8px 22px; border: 1px solid var(--gray-300); border-radius: 30px; font-size: 13px; font-weight: 600; cursor: pointer; background: var(--white); color: var(--gray-600); transition: var(--transition-base); }
        .doc-tab.active { border-color: var(--primary); background: var(--primary); color: var(--white); }
        .doc-tab:hover { border-color: var(--primary); color: var(--primary); }
        .doc-tab.active:hover { color: var(--white); }
        .documents-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
        .doc-card { background: var(--gray-50); border: 1px solid var(--gray-200); border-radius: var(--radius-md); padding: 20px; display: flex; align-items: flex-start; gap: 15px; transition: var(--transition-base); cursor: pointer; }
        .doc-card:hover { border-color: var(--primary); box-shadow: var(--shadow-md); }
        .doc-card .doc-icon { width: 50px; height: 50px; flex-shrink: 0; background: var(--primary-light); border-radius: 12px; display: flex; align-items: center; justify-content: center; font-size: 22px; color: var(--primary); }
        .doc-card .doc-content { flex: 1; }
        .doc-card h4 { font-size: 14px; font-weight: 700; margin-bottom: 4px; color: var(--gray-900); }
        .doc-card p { font-size: 12px; color: var(--gray-500); margin-bottom: 6px; }
        .doc-card .doc-meta { font-size: 10px; color: var(--gray-400); display: flex; gap: 8px; }
        .doc-card .doc-action { font-size: 12px; font-weight: 700; color: var(--primary); text-decoration: none; }

        .b2b-section { padding: 40px 0; background: var(--gray-50); border-top: 1px solid var(--gray-200); border-bottom: 1px solid var(--gray-200); }
        .b2b-content { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; max-width: 1100px; margin: 0 auto; }
        .b2b-info h2 { font-size: 28px; font-weight: 800; color: var(--gray-900); margin-bottom: 16px; }
        .b2b-info p { color: var(--gray-600); font-size: 15px; line-height: 1.7; margin-bottom: 20px; }
        .b2b-info .features { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .b2b-info .features .item { background: var(--white); border: 1px solid var(--gray-200); border-radius: var(--radius-md); padding: 14px 16px; text-align: center; }
        .b2b-info .features .item .icon { font-size: 24px; display: block; margin-bottom: 4px; }
        .b2b-info .features .item span { font-size: 13px; color: var(--gray-700); font-weight: 500; }
        .b2b-form { background: var(--white); border: 1px solid var(--gray-200); border-radius: var(--radius-md); padding: 28px; }
        .b2b-form h3 { font-size: 18px; font-weight: 700; color: var(--gray-900); margin-bottom: 16px; }
        .b2b-form .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
        .b2b-form input, .b2b-form select, .b2b-form textarea { width: 100%; padding: 10px 14px; border: 1px solid var(--gray-300); border-radius: var(--radius-sm); background: var(--white); color: var(--gray-900); font-family: inherit; font-size: 13px; transition: var(--transition-base); }
        .b2b-form input:focus, .b2b-form select:focus, .b2b-form textarea:focus { outline: none; border-color: var(--primary); }
        .b2b-form textarea { resize: vertical; min-height: 80px; }
        .b2b-form .btn { width: 100%; margin-top: 12px; }

        .library-section { background: var(--gray-50); padding: 40px 0; border-top: 1px solid var(--gray-200); border-bottom: 1px solid var(--gray-200); }
        .library-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; max-width: 1000px; margin: 0 auto; }
        .library-card { background: var(--white); border: 1px solid var(--gray-200); border-radius: var(--radius-md); padding: 20px 16px; transition: var(--transition-base); cursor: pointer; }
        .library-card:hover { border-color: var(--primary); transform: translateY(-4px); box-shadow: var(--shadow-md); }
        .library-card .icon { font-size: 30px; display: block; margin-bottom: 8px; }
        .library-card h3 { font-size: 14px; font-weight: 700; margin-bottom: 4px; color: var(--gray-900); }
        .library-card p { font-size: 12px; color: var(--gray-500); margin-bottom: 8px; }
        .library-card .meta { font-size: 10px; color: var(--gray-500); display: flex; gap: 8px; flex-wrap: wrap; }
        .library-card .meta .tag-sm { padding: 2px 8px; border-radius: 12px; font-size: 9px; font-weight: 600; background: var(--primary-light); color: var(--primary); }

        .reviews-section { padding: 40px 0; background: var(--white); }
        .reviews-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; max-width: 1000px; margin: 0 auto; }
        .review-card { background: var(--gray-50); border: 1px solid var(--gray-200); border-radius: var(--radius-md); padding: 18px; transition: var(--transition-base); }
        .review-card:hover { border-color: var(--primary); transform: translateY(-2px); }
        .review-card .review-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 4px; }
        .review-card .review-header .name { font-weight: 600; color: var(--gray-900); font-size: 13px; }
        .review-card .review-header .date { font-size: 10px; color: var(--gray-500); }
        .review-card .review-stars { color: var(--secondary); font-size: 13px; letter-spacing: 1px; margin-bottom: 4px; }
        .review-card .review-text { font-size: 12px; color: var(--gray-600); line-height: 1.6; }
        .review-card .review-product { font-size: 10px; color: var(--gray-500); margin-top: 6px; padding-top: 6px; border-top: 1px solid var(--gray-200); }

        .contacts-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 28px; margin-top: 20px; max-width: 1000px; margin-left: auto; margin-right: auto; }
        .contacts-info p { margin-bottom: 6px; font-size: 14px; color: var(--gray-600); }
        .contacts-info strong { font-weight: 700; color: var(--gray-900); }
        .contacts-info a { color: var(--primary); text-decoration: none; transition: var(--transition-base); }
        .contacts-info a:hover { color: var(--primary-dark); text-decoration: underline; }
        .contacts-form { background: var(--white); padding: 24px; border-radius: var(--radius-md); border: 1px solid var(--gray-200); }
        .contacts-form h3 { font-size: 16px; font-weight: 700; margin-bottom: 12px; color: var(--gray-900); }
        .contacts-form input, .contacts-form textarea { width: 100%; padding: 10px 14px; border: 2px solid var(--gray-300); border-radius: var(--radius-sm); margin-bottom: 10px; font-family: inherit; font-size: 13px; transition: var(--transition-base); background: var(--white); color: var(--gray-900); }
        .contacts-form input:focus, .contacts-form textarea:focus { outline: none; border-color: var(--primary); }
        .contacts-form textarea { resize: vertical; }
        .contacts-form .btn { width: 100%; }

        .footer { background: var(--gray-900); color: var(--white); padding: 36px 0 20px; border-top: 1px solid var(--gray-800); margin-top: 40px; }
        .footer-grid { display: grid; grid-template-columns: 2fr 1fr 1fr 1fr; gap: 28px; }
        .footer a { color: var(--gray-500); transition: var(--transition-base); text-decoration: none; font-size: 13px; }
        .footer a:hover { color: var(--secondary); }
        .footer h4 { font-size: 14px; font-weight: 700; margin-bottom: 10px; color: var(--white); letter-spacing: 0.02em; }
        .footer p { color: var(--gray-500); font-size: 13px; margin: 4px 0; }
        .footer .logo { display: flex; align-items: center; gap: 8px; color: var(--white); text-decoration: none; }
        .footer .logo .logo-mark { width: 36px; height: 36px; }
        .footer .logo .logo-text .mr { color: var(--secondary); }
        .footer .logo .logo-text .fix { color: var(--white); }
        .footer .logo-desc { color: var(--gray-500); margin-top: 4px; font-size: 13px; }
        .footer-bottom { border-top: 1px solid rgba(255,255,255,0.06); padding-top: 16px; margin-top: 20px; text-align: center; font-size: 13px; color: var(--gray-500); }

        .elfsight-app-c7586e28-f9a3-4b17-a597-61aeb2b7fe8a { max-width: 1400px; margin: 0 auto; padding: 20px 0; }
        .eapps-logo-showcase__container, .elfsight-app-c7586e28-f9a3-4b17-a597-61aeb2b7fe8a .eapps-logo-showcase__container { background: transparent !important; }
        .eapps-logo-showcase__item-logo img { filter: grayscale(100%) brightness(200%); transition: 0.3s; }
        .eapps-logo-showcase__item-logo img:hover { filter: none; }
        .eapps-logo-showcase__item-description { color: #bbbbbb !important; font-size: 12px; }
        .eapps-logo-showcase__item-title { color: #ffffff !important; font-size: 14px; font-weight: 600; }

        .notification { position: fixed; bottom: 90px; left: 50%; transform: translateX(-50%); background: var(--gray-900); color: var(--white); padding: 12px 24px; border-radius: var(--radius-md); font-weight: 600; z-index: 9999; box-shadow: var(--shadow-lg); transition: opacity 0.3s ease; font-size: 14px; text-align: center; border: 1px solid var(--gray-700); }

        .reveal { opacity: 0; transform: translateY(30px); transition: all 0.7s cubic-bezier(0.2, 0.9, 0.3, 1); }
        .reveal.visible { opacity: 1; transform: translateY(0); }
        .reveal-1 { transition-delay: 0.05s; }
        .reveal-2 { transition-delay: 0.10s; }
        .reveal-3 { transition-delay: 0.15s; }
        .reveal-4 { transition-delay: 0.20s; }

        .ai-agent-toggle { position: fixed; bottom: 100px; right: 24px; z-index: 900; width: 64px; height: 64px; border-radius: 50%; background: linear-gradient(135deg, var(--primary), var(--primary-dark)); color: var(--white); border: 3px solid var(--secondary); cursor: pointer; box-shadow: 0 4px 30px rgba(204,0,0,0.4); transition: var(--transition-base); display: flex; align-items: center; justify-content: center; padding: 0; }
        .ai-agent-toggle:hover { transform: scale(1.08); box-shadow: 0 8px 40px rgba(204,0,0,0.5); }
        .ai-agent-toggle svg { width: 100%; height: 100%; border-radius: 50%; }
        .ai-agent-toggle .pulse-ring { position: absolute; width: 74px; height: 74px; border-radius: 50%; background: rgba(204,0,0,0.2); animation: pulseRing 2s ease-out infinite; pointer-events: none; top: -5px; right: -5px; }
        @keyframes pulseRing { 0% { transform: scale(0.8); opacity: 0.8; } 100% { transform: scale(1.6); opacity: 0; } }

        .ai-agent-window { display: none; position: fixed; bottom: 180px; right: 24px; width: 440px; max-height: 620px; background: var(--white); border: 1px solid var(--gray-200); border-radius: var(--radius-lg); box-shadow: var(--shadow-xl); z-index: 901; flex-direction: column; overflow: hidden; animation: slideUp 0.3s ease; }
        .ai-agent-window.open { display: flex; }
        @keyframes slideUp { from { transform: translateY(20px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }

        .ai-agent-header { background: linear-gradient(135deg, var(--primary), var(--primary-dark)); color: var(--white); padding: 14px 20px; display: flex; justify-content: space-between; align-items: center; flex-shrink: 0; }
        .ai-agent-header h4 { font-weight: 600; font-size: 15px; display: flex; align-items: center; gap: 10px; }
        .ai-agent-header h4 .avatar { width: 36px; height: 36px; border-radius: 50%; background: var(--secondary); display: flex; align-items: center; justify-content: center; overflow: hidden; border: 2px solid rgba(255,255,255,0.4); }
        .ai-agent-header h4 .avatar svg { width: 100%; height: 100%; }
        .ai-agent-header .status { font-size: 11px; opacity: 0.9; display: flex; align-items: center; gap: 6px; }
        .ai-agent-header .status .dot { width: 8px; height: 8px; border-radius: 50%; display: inline-block; background: var(--secondary); animation: blink 1s infinite; }
        @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0.3; } }
        .ai-agent-header button { background: none; border: none; color: var(--white); font-size: 22px; cursor: pointer; opacity: 0.7; transition: var(--transition-base); }
        .ai-agent-header button:hover { opacity: 1; }

        .ai-agent-messages { flex: 1; overflow-y: auto; padding: 16px 20px; max-height: 380px; background: var(--gray-50); }
        .ai-agent-messages::-webkit-scrollbar { width: 4px; }
        .ai-agent-messages::-webkit-scrollbar-thumb { background: var(--gray-300); border-radius: 2px; }

        .ai-msg { margin-bottom: 12px; padding: 10px 16px; border-radius: 14px; max-width: 88%; font-size: 13px; line-height: 1.5; animation: msgIn 0.3s ease; white-space: pre-wrap; }
        @keyframes msgIn { from { transform: scale(0.9); opacity: 0; } to { transform: scale(1); opacity: 1; } }
        .ai-msg.user { background: var(--gray-200); color: var(--gray-900); align-self: flex-end; margin-left: auto; border-bottom-right-radius: 4px; }
        .ai-msg.bot { background: linear-gradient(135deg, var(--primary), var(--primary-dark)); color: var(--white); border-bottom-left-radius: 4px; }
        .ai-msg.bot .typing { display: inline-block; animation: typing 1.2s infinite; }
        @keyframes typing { 0%, 20% { opacity: 0; } 40%, 60% { opacity: 1; } 80%, 100% { opacity: 0; } }

        .ai-agent-input { display: flex; padding: 10px 14px; border-top: 1px solid var(--gray-200); background: var(--white); gap: 8px; flex-shrink: 0; flex-wrap: wrap; }
        .ai-agent-input input { flex: 1; padding: 10px 14px; border: 1px solid var(--gray-300); border-radius: var(--radius-md); background: var(--white); color: var(--gray-900); font-family: inherit; font-size: 13px; transition: var(--transition-base); min-width: 100px; }
        .ai-agent-input input:focus { outline: none; border-color: var(--primary); }
        .ai-agent-input .voice-btn { background: var(--gray-100); color: var(--gray-600); border: none; border-radius: var(--radius-md); padding: 8px 12px; cursor: pointer; font-size: 16px; transition: var(--transition-base); }
        .ai-agent-input .voice-btn:hover { background: var(--primary-light); color: var(--primary); }
        .ai-agent-input .voice-btn.active { background: var(--primary); color: var(--white); animation: pulseGlow 1.2s ease-in-out infinite; }
        @keyframes pulseGlow { 0%, 100% { box-shadow: 0 0 0 0 rgba(204,0,0,0.3); } 50% { box-shadow: 0 0 0 12px rgba(204,0,0,0); } }
        .ai-agent-input .send-btn { background: var(--primary); color: var(--white); border: none; border-radius: var(--radius-md); padding: 8px 16px; cursor: pointer; font-size: 16px; transition: var(--transition-base); }
        .ai-agent-input .send-btn:hover { background: var(--primary-dark); }

        .ai-agent-suggestions { display: flex; flex-wrap: wrap; gap: 6px; padding: 8px 14px; border-top: 1px solid var(--gray-200); background: var(--gray-50); }
        .ai-agent-suggestions .chip { padding: 4px 12px; border: 1px solid var(--gray-300); border-radius: 20px; font-size: 11px; color: var(--gray-600); cursor: pointer; transition: var(--transition-base); background: var(--white); }
        .ai-agent-suggestions .chip:hover { border-color: var(--primary); color: var(--primary); background: var(--primary-light); }

        @media (max-width: 1024px) {
            .catalog-grid { grid-template-columns: repeat(2, 1fr); }
            .tasks-grid { grid-template-columns: repeat(2, 1fr); }
            .reviews-grid { grid-template-columns: repeat(2, 1fr); }
            .library-grid { grid-template-columns: repeat(2, 1fr); }
            .b2b-content { grid-template-columns: 1fr; }
            .b2b-info .features { grid-template-columns: 1fr 1fr; }
            .hero h1 { font-size: 32px; }
            .ai-agent-window { width: 380px; }
            .documents-grid { grid-template-columns: repeat(2, 1fr); }
        }
        @media (max-width: 992px) {
            .header .container { flex-wrap: wrap; }
            .nav { display: none; width: 100%; flex-direction: column; align-items: flex-start; padding: 10px 0 6px; gap: 10px; border-top: 1px solid var(--gray-200); margin-top: 6px; }
            .nav.open { display: flex; }
            .burger { display: block; }
            .hero-grid { grid-template-columns: 1fr; gap: 28px; }
            .hero h1 { font-size: 28px; }
            .benefits-grid { grid-template-columns: 1fr 1fr; }
            .footer-grid { grid-template-columns: 1fr 1fr; gap: 20px; }
            .contacts-grid { grid-template-columns: 1fr; gap: 20px; }
        }
        @media (max-width: 768px) {
            .container { padding: 0 16px; }
            .hero { padding: 90px 0 30px; }
            .hero h1 { font-size: 24px; }
            .hero-desc { font-size: 14px; }
            .hero-stats { grid-template-columns: 1fr 1fr; gap: 8px; }
            .stat-item { padding: 12px; }
            .stat-number { font-size: 22px; }
            .catalog-grid { grid-template-columns: 1fr 1fr; gap: 14px; }
            .tasks-grid { grid-template-columns: 1fr; }
            .benefits-grid { grid-template-columns: 1fr; }
            .reviews-grid { grid-template-columns: 1fr; }
            .library-grid { grid-template-columns: 1fr; }
            .b2b-info .features { grid-template-columns: 1fr; }
            .b2b-form .form-row { grid-template-columns: 1fr; }
            .header-actions .phone { display: none; }
            .search-container { flex-direction: column; }
            .search-container .btn { width: 100%; }
            .price-toolbar { flex-direction: column; align-items: stretch; }
            .price-toolbar .count { margin-left: 0; }
            .price-table { font-size: 11px; min-width: 550px; }
            .price-table th, .price-table td { padding: 4px 8px; }
            .ai-agent-window { position: fixed; top: 0; left: 0; right: 0; bottom: 0; width: 100vw; max-height: 100vh; height: 100vh; border-radius: 0; z-index: 9999; }
            .ai-agent-header { padding: 16px 20px; border-radius: 0; }
            .ai-agent-header h4 { font-size: 17px; }
            .ai-agent-header h4 .avatar { width: 42px; height: 42px; }
            .ai-agent-messages { max-height: none; flex: 1; padding: 16px 16px 20px; }
            .ai-msg { max-width: 92%; font-size: 14px; padding: 12px 16px; }
            .ai-agent-suggestions { padding: 10px 14px; overflow-x: auto; flex-wrap: nowrap; -webkit-overflow-scrolling: touch; }
            .ai-agent-suggestions .chip { white-space: nowrap; flex-shrink: 0; font-size: 12px; padding: 8px 16px; }
            .ai-agent-input { padding: 12px 14px; padding-bottom: calc(12px + env(safe-area-inset-bottom)); }
            .ai-agent-input input { padding: 12px 16px; font-size: 16px; }
            .ai-agent-input .voice-btn, .ai-agent-input .send-btn { padding: 12px 16px; font-size: 18px; }
            .ai-agent-toggle { bottom: 20px; right: 16px; width: 60px; height: 60px; }
            .ai-agent-toggle .pulse-ring { width: 70px; height: 70px; }
            .payment-grid { grid-template-columns: 1fr; }
            .documents-grid { grid-template-columns: 1fr; }
        }
        @media (max-width: 480px) {
            .catalog-grid { grid-template-columns: 1fr; }
            .hero h1 { font-size: 20px; }
            .hero-actions .btn { width: 100%; justify-content: center; }
            .price-table { min-width: 420px; font-size: 10px; }
            .price-table th, .price-table td { padding: 3px 6px; }
            .ai-agent-messages { padding: 12px 12px 16px; }
            .ai-msg { font-size: 13px; padding: 10px 14px; }
            .ai-agent-header { padding: 12px 16px; }
            .ai-agent-input { padding: 10px 12px; }
        }
    </style>
</head>
<body>

<header class="header" id="header">
    <div class="container">
        <a href="#" class="logo">
            <div class="logo-mark">
                <svg viewBox="0 0 44 44" xmlns="http://www.w3.org/2000/svg">
                    <rect x="8" y="14" width="28" height="22" rx="4" fill="#CC0000"/>
                    <rect x="18" y="6" width="8" height="10" rx="2" fill="#CC0000"/>
                    <rect x="20" y="4" width="4" height="4" rx="1" fill="#FFCC00"/>
                    <circle cx="18" cy="22" r="2" fill="#FFFFFF"/>
                    <circle cx="26" cy="22" r="2" fill="#FFFFFF"/>
                    <circle cx="18.5" cy="22.5" r="0.8" fill="#1A1E24"/>
                    <circle cx="26.5" cy="22.5" r="0.8" fill="#1A1E24"/>
                    <path d="M18 28 Q22 31 26 28" stroke="#FFFFFF" stroke-width="1.5" fill="none" stroke-linecap="round"/>
                    <rect x="12" y="10" width="20" height="5" rx="2" fill="#FFCC00"/>
                    <rect x="10" y="12" width="24" height="3" rx="1" fill="#FFCC00"/>
                    <rect x="10" y="16" width="3" height="16" rx="1" fill="rgba(255,255,255,0.3)"/>
                </svg>
            </div>
            <div>
                <span class="logo-text"><span class="mr">MR.</span><span class="fix">FIX</span></span>
                <div class="logo-sub">Герметик • Клей • Крепёж</div>
            </div>
        </a>
        <button class="burger" onclick="document.getElementById('main-nav').classList.toggle('open')">☰</button>
        <nav class="nav" id="main-nav">
            <a href="#" class="active">Главная</a>
            <a href="#price">Прайс-лист</a>
            <a href="#documents">Документы</a>
            <a href="#payment">Оплата</a>
            <a href="#library">Библиотека</a>
            <a href="#reviews">Отзывы</a>
            <a href="#b2b">B2B</a>
            <a href="#contacts">Контакты</a>
        </nav>
        <div class="header-actions">
            <a href="tel:+375296885400" class="phone">+375 (29) 688-54-00</a>
            <a href="#payment" class="btn btn-primary btn-sm"><i class="fas fa-building"></i> Оплата</a>
            <button class="cart-btn" onclick="showNotification('🛒 Корзина пуста. Добавьте товары!')">
                <i class="fas fa-shopping-cart"></i>
                <span class="cart-count" id="cartCount">0</span>
            </button>
        </div>
    </div>
</header>

<section class="hero">
    <div class="container">
        <div class="hero-grid">
            <div>
                <span class="hero-badge"><i class="fas fa-robot"></i> Умный ИИ-помощник</span>
                <h1>Герметик, клей и крепёж — <span class="highlight">всё, что держит мир вместе</span></h1>
                <div class="hero-quote">«Есть ли у меня план? У меня их три. И ещё один — про запас.»<br>— Mr. Fix</div>
                <p class="hero-desc">Опишите задачу — Mr. Fix задаст пару вопросов, пошутит и подберёт идеальное решение. Более 100 товаров, 23 бренда, 98% успешных подборов.</p>
                <div class="hero-actions" style="margin-top:16px;">
                    <a href="#" class="btn btn-primary" onclick="document.getElementById('aiToggle').click(); return false;"><i class="fas fa-comments"></i> Спросить Mr. Fix</a>
                    <a href="#price" class="btn btn-outline"><i class="fas fa-file-invoice"></i> Прайс-лист</a>
                    <a href="#documents" class="btn btn-outline"><i class="fas fa-file-contract"></i> Документы</a>
                </div>
            </div>
            <div>
                <div class="hero-stats">
                    <div class="stat-item"><span class="stat-number">100+</span><span class="stat-label">товаров</span></div>
                    <div class="stat-item"><span class="stat-number">23</span><span class="stat-label">бренда</span></div>
                    <div class="stat-item"><span class="stat-number">98%</span><span class="stat-label">подборов</span></div>
                    <div class="stat-item"><span class="stat-number">4.8</span><span class="stat-label">рейтинг</span></div>
                </div>
            </div>
        </div>
    </div>
</section>

<section class="search-section">
    <div class="container">
        <h2>Умный поиск материалов</h2>
        <p class="sub">Опишите задачу — Mr. Fix подберёт решение</p>
        <div class="smart-search">
            <div class="search-container">
                <input type="text" id="smart-search-input" placeholder="Например: заделать шов в ванной, повесить полку, склеить пластик...">
                <button class="btn btn-primary" onclick="searchCatalog()"><i class="fas fa-search"></i> Найти</button>
            </div>
            <div class="search-tags">
                <a href="#" class="tag" onclick="searchTag('герметик')">#Герметик</a>
                <a href="#" class="tag" onclick="searchTag('клей')">#Клей</a>
                <a href="#" class="tag" onclick="searchTag('пена')">#Клей-пена</a>
                <a href="#" class="tag" onclick="searchTag('силикон')">#Силикон</a>
                <a href="#" class="tag" onclick="searchTag('эпоксид')">#Эпоксид</a>
                <a href="#" class="tag" onclick="searchTag('СИЗ')">#СИЗ</a>
            </div>
        </div>
    </div>
</section>

<section class="section" style="padding:30px 0;">
    <div class="container">
        <h2 class="section-title">Три плана Mr. Fix</h2>
        <p class="section-sub">Каждая задача — отдельный план</p>
        <div class="tasks-grid">
            <div class="task-card reveal reveal-1">
                <span class="task-icon">🧪</span>
                <h3>План А — Герметик</h3>
                <p>Защитить, заизолировать, закрыть шов. Силикон, акрил, полиуретан.</p>
                <a href="#price" class="btn btn-outline btn-sm" onclick="searchTag('герметик')">Подобрать герметик</a>
            </div>
            <div class="task-card reveal reveal-2">
                <span class="task-icon">🔧</span>
                <h3>План Б — Клей</h3>
                <p>Соединить, склеить, зафиксировать. MS-полимер, пена, эпоксид.</p>
                <a href="#price" class="btn btn-outline btn-sm" onclick="searchTag('клей')">Подобрать клей</a>
            </div>
            <div class="task-card reveal reveal-3">
                <span class="task-icon">🔩</span>
                <h3>План В — Крепёж</h3>
                <p>Прикрутить, закрепить, повесить. Дюбели, саморезы, анкеры.</p>
                <a href="#price" class="btn btn-outline btn-sm" onclick="searchTag('крепёж')">Найти крепёж</a>
            </div>
        </div>
    </div>
</section>

<section class="section" style="background:var(--gray-100); border-top:1px solid var(--gray-200); border-bottom:1px solid var(--gray-200); padding:30px 0;">
    <div class="container">
        <h2 class="section-title">Почему Mr. Fix</h2>
        <div class="benefits-grid">
            <div class="benefit-card reveal reveal-1"><span class="benefit-icon">🤖</span><h3>Умный ИИ-помощник</h3><p>Задаст вопросы и подберёт точно</p></div>
            <div class="benefit-card reveal reveal-2"><span class="benefit-icon">📦</span><h3>100+ материалов</h3><p>Герметики, клеи, пены, затирки, СИЗ</p></div>
            <div class="benefit-card reveal reveal-3"><span class="benefit-icon">✅</span><h3>98% успешных подборов</h3><p>Точное решение под задачу</p></div>
            <div class="benefit-card reveal reveal-4"><span class="benefit-icon">😄</span><h3>С юмором, но всерьёз</h3><p>Шутим в начале — держим в конце</p></div>
        </div>
    </div>
</section>

<section class="section" id="catalog" style="padding:30px 0;">
    <div class="container">
        <div class="section-header">
            <h2><i class="fas fa-th"></i> Популярные товары</h2>
            <a href="#price" class="btn btn-outline btn-sm">Смотреть все →</a>
        </div>
        <div class="catalog-grid" id="catalogGrid"></div>
    </div>
</section>

<section class="price-section" id="price">
    <div class="container">
        <div class="section-header">
            <h2><i class="fas fa-file-invoice"></i> Прайс-лист <span class="badge" id="priceBadge">100+ товаров</span></h2>
            <div>
                <button class="btn btn-secondary btn-sm" onclick="exportCSV()"><i class="fas fa-file-csv"></i> CSV</button>
                <button class="btn btn-primary btn-sm" onclick="showNotification('📄 PDF экспорт в разработке')"><i class="fas fa-file-pdf"></i> PDF</button>
            </div>
        </div>
        <div class="price-toolbar">
            <input type="text" id="searchInput" placeholder="🔍 Поиск по названию, артикулу, бренду..." oninput="filterPrice()">
            <select id="categoryFilter" onchange="filterPrice()">
                <option value="all">Все категории</option>
            </select>
            <span class="count" id="rowCount">Показано: 0</span>
        </div>
        <div class="price-accordion" id="priceAccordion"></div>
    </div>
</section>

<section class="payment-section" id="payment">
    <div class="container">
        <h2 class="section-title">Оплата и доставка</h2>
        <p class="section-sub">Удобные способы для частных лиц и компаний</p>
        <div class="payment-grid">
            <div class="payment-card reveal reveal-1"><span class="icon">💳</span><h3>Оплата картой онлайн</h3><p>Принимаем Visa, MasterCard, Белкарт и ЕРИП. Безопасные транзакции.</p></div>
            <div class="payment-card reveal reveal-2"><span class="icon">📄</span><h3>Безналичный расчет</h3><p>Для юрлиц: счет-фактура, договор, отсрочка платежа. Полный пакет документов.</p></div>
            <div class="payment-card reveal reveal-3"><span class="icon">🚚</span><h3>Доставка по РБ</h3><p>Курьером по Минску, транспортными компаниями по всей Беларуси. Отправка в день заказа.</p></div>
        </div>
    </div>
</section>

<section class="documents-section" id="documents">
    <div class="container">
        <h2 class="section-title">Документы и сертификаты</h2>
        <p class="section-sub">Вся необходимая документация для проверки качества</p>
        <div class="doc-tabs">
            <button class="doc-tab active" onclick="filterDocs('all', this)">Все</button>
            <button class="doc-tab" onclick="filterDocs('Сертификат', this)">Сертификаты</button>
            <button class="doc-tab" onclick="filterDocs('Паспорт качества', this)">Паспорта качества</button>
            <button class="doc-tab" onclick="filterDocs('Декларация', this)">Декларации</button>
        </div>
        <div class="documents-grid" id="documentsGrid">
            <div class="doc-card" data-type="Сертификат" onclick="showNotification('📄 Файл скачивается...')">
                <div class="doc-icon"><i class="fas fa-certificate"></i></div>
                <div class="doc-content"><h4>Сертификат соответствия MS-полимеры</h4><p>Сертификат на линейку гибридных клеев FÖCH, Soudal, Tytan.</p><div class="doc-meta"><span>PDF</span><span>1.2 МБ</span></div></div>
                <i class="fas fa-download doc-action" style="margin-top:5px;"></i>
            </div>
            <div class="doc-card" data-type="Паспорт качества" onclick="showNotification('📄 Файл скачивается...')">
                <div class="doc-icon"><i class="fas fa-file-invoice"></i></div>
                <div class="doc-content"><h4>Паспорт качества Sika</h4><p>Паспорт на полиуретановые герметики и клеи Sika.</p><div class="doc-meta"><span>PDF</span><span>2.1 МБ</span></div></div>
                <i class="fas fa-download doc-action" style="margin-top:5px;"></i>
            </div>
            <div class="doc-card" data-type="Декларация" onclick="showNotification('📄 Файл скачивается...')">
                <div class="doc-icon"><i class="fas fa-file-signature"></i></div>
                <div class="doc-content"><h4>Декларация соответствия СИЗ</h4><p>Декларация на средства индивидуальной защиты из каталога.</p><div class="doc-meta"><span>PDF</span><span>1.8 МБ</span></div></div>
                <i class="fas fa-download doc-action" style="margin-top:5px;"></i>
            </div>
            <div class="doc-card" data-type="Сертификат" onclick="showNotification('📄 Файл скачивается...')">
                <div class="doc-icon"><i class="fas fa-certificate"></i></div>
                <div class="doc-content"><h4>Сертификат соответствия Ceresit</h4><p>Сертификат на строительные смеси и герметики Ceresit.</p><div class="doc-meta"><span>PDF</span><span>1.5 МБ</span></div></div>
                <i class="fas fa-download doc-action" style="margin-top:5px;"></i>
            </div>
            <div class="doc-card" data-type="Паспорт качества" onclick="showNotification('📄 Файл скачивается...')">
                <div class="doc-icon"><i class="fas fa-file-invoice"></i></div>
                <div class="doc-content"><h4>Паспорт качества Mapei</h4><p>Паспорт на эпоксидные затирки и клеи Mapei.</p><div class="doc-meta"><span>PDF</span><span>3.2 МБ</span></div></div>
                <i class="fas fa-download doc-action" style="margin-top:5px;"></i>
            </div>
            <div class="doc-card" data-type="Декларация" onclick="showNotification('📄 Файл скачивается...')">
                <div class="doc-icon"><i class="fas fa-file-signature"></i></div>
                <div class="doc-content"><h4>Декларация на ЛКМ</h4><p>Декларация соответствия на химические составы и краски.</p><div class="doc-meta"><span>PDF</span><span>2.5 МБ</span></div></div>
                <i class="fas fa-download doc-action" style="margin-top:5px;"></i>
            </div>
        </div>
    </div>
</section>

<section class="b2b-section" id="b2b">
    <div class="container">
        <h2 style="text-align:center; font-size:28px; font-weight:800; color:var(--gray-900); margin-bottom:6px;"><i class="fas fa-building"></i> B2B — Оптовые поставки</h2>
        <p style="text-align:center; font-size:15px; color:var(--gray-500); margin-bottom:28px;">Специальные условия для бизнеса и производства</p>
        <div class="b2b-content">
            <div class="b2b-info">
                <h2>Экономьте до 30% на материалах</h2>
                <p>Мы работаем напрямую с производителями и предлагаем выгодные оптовые цены для строительных компаний, производств и ремонтных организаций.</p>
                <div class="features">
                    <div class="item"><span class="icon">📦</span><span>Прямые поставки</span></div>
                    <div class="item"><span class="icon">💰</span><span>Скидки от 10%</span></div>
                    <div class="item"><span class="icon">🚚</span><span>Доставка по РБ</span></div>
                    <div class="item"><span class="icon">📄</span><span>Документы для юрлиц</span></div>
                </div>
            </div>
            <div class="b2b-form">
                <h3><i class="fas fa-paper-plane"></i> Запрос оптовых условий</h3>
                <form onsubmit="submitB2B(event)">
                    <div class="form-row">
                        <input type="text" id="b2bName" placeholder="Контактное лицо" required>
                        <input type="text" id="b2bCompany" placeholder="Компания" required>
                    </div>
                    <div class="form-row">
                        <input type="tel" id="b2bPhone" placeholder="Телефон" required>
                        <input type="email" id="b2bEmail" placeholder="Email" required>
                    </div>
                    <select id="b2bInterest">
                        <option value="">Что вас интересует?</option>
                        <option>Гибридные клеи (MS)</option>
                        <option>Полиуретановые клеи (пена)</option>
                        <option>Силиконовые герметики</option>
                        <option>Акриловые герметики</option>
                        <option>Эпоксидные затирки</option>
                        <option>СИЗ</option>
                        <option>Весь ассортимент</option>
                    </select>
                    <textarea id="b2bComment" placeholder="Дополнительная информация: объём, сроки, особые требования..."></textarea>
                    <button type="submit" class="btn btn-primary"><i class="fas fa-paper-plane"></i> Отправить запрос</button>
                </form>
            </div>
        </div>
    </div>
</section>

<section class="library-section" id="library">
    <div class="container">
        <h2 style="text-align:center; font-size:26px; font-weight:800; color:var(--gray-900); margin-bottom:6px;">📚 База знаний Mr. Fix</h2>
        <p style="text-align:center; font-size:14px; color:var(--gray-500); margin-bottom:24px;">Планы, инструкции и решения</p>
        <div class="library-grid" id="libraryGrid"></div>
    </div>
</section>

<section class="reviews-section" id="reviews">
    <div class="container">
        <h2 style="text-align:center; font-size:26px; font-weight:800; color:var(--gray-900); margin-bottom:6px;">⭐ Отзывы клиентов</h2>
        <p style="text-align:center; font-size:14px; color:var(--gray-500); margin-bottom:24px;">Реальные отзывы о качестве и сервисе</p>
        <div class="reviews-grid" id="reviewsGrid"></div>
    </div>
</section>

<section class="section" id="contacts" style="padding:30px 0;">
    <div class="container">
        <h2 class="section-title">Контакты</h2>
        <div class="contacts-grid">
            <div class="contacts-info">
                <p><strong>📍 Адрес:</strong> г. Минск, ул. Шаранговича, д. 21, пом. 207</p>
                <p><strong>🕒 График:</strong> Пн–Пт: 09:00–18:00</p>
                <p><strong>📞 Телефон:</strong> <a href="tel:+375296885400">+375 (29) 688-54-00</a></p>
                <p><strong>✉️ Email:</strong> <a href="mailto:monotop2010@mail.ru">monotop2010@mail.ru</a></p>
                <div style="margin-top:14px; display:flex; gap:10px; flex-wrap:wrap;">
                    <a href="#" class="btn btn-primary btn-sm"><i class="fab fa-whatsapp"></i> WhatsApp</a>
                    <a href="#" class="btn btn-outline btn-sm"><i class="fas fa-phone"></i> Позвонить</a>
                </div>
            </div>
            <div class="contacts-form">
                <h3><i class="fas fa-envelope"></i> Напишите нам</h3>
                <form onsubmit="alert('Сообщение отправлено!'); return false;">
                    <input type="text" placeholder="Ваше имя" required>
                    <input type="tel" placeholder="Телефон" required>
                    <textarea placeholder="Сообщение" rows="4" required></textarea>
                    <button type="submit" class="btn btn-primary"><i class="fas fa-paper-plane"></i> Отправить</button>
                </form>
            </div>
        </div>
    </div>
</section>

<footer class="footer">
    <div class="container footer-grid">
        <div>
            <a href="#" class="logo">
                <div class="logo-mark">
                    <svg viewBox="0 0 44 44" xmlns="http://www.w3.org/2000/svg">
                        <rect x="8" y="14" width="28" height="22" rx="4" fill="#CC0000"/>
                        <rect x="18" y="6" width="8" height="10" rx="2" fill="#CC0000"/>
                        <rect x="20" y="4" width="4" height="4" rx="1" fill="#FFCC00"/>
                        <circle cx="18" cy="22" r="2" fill="#FFFFFF"/>
                        <circle cx="26" cy="22" r="2" fill="#FFFFFF"/>
                        <circle cx="18.5" cy="22.5" r="0.8" fill="#1A1E24"/>
                        <circle cx="26.5" cy="22.5" r="0.8" fill="#1A1E24"/>
                        <path d="M18 28 Q22 31 26 28" stroke="#FFFFFF" stroke-width="1.5" fill="none" stroke-linecap="round"/>
                        <rect x="12" y="10" width="20" height="5" rx="2" fill="#FFCC00"/>
                    </svg>
                </div>
                <span class="logo-text"><span class="mr">MR.</span><span class="fix">FIX</span></span>
            </a>
            <p class="logo-desc">Умный помощник: герметик, клей, крепёж. «Есть ли у меня план? У меня их три.»</p>
        </div>
        <div>
            <h4>Контакты</h4>
            <p>📍 Минск, Шаранговича 21/207</p>
            <p>📞 <a href="tel:+375296885400">+375 (29) 688-54-00</a></p>
            <p>✉️ <a href="mailto:monotop2010@mail.ru">monotop2010@mail.ru</a></p>
        </div>
        <div>
            <h4>Разделы</h4>
            <p><a href="#price">Прайс-лист</a></p>
            <p><a href="#payment">Оплата</a></p>
            <p><a href="#documents">Документы</a></p>
            <p><a href="#library">Библиотека</a></p>
            <p><a href="#contacts">Контакты</a></p>
        </div>
        <div>
            <h4>Информация</h4>
            <p><a href="#">Политика конфиденциальности</a></p>
            <p><a href="#payment">Доставка и оплата</a></p>
        </div>
    </div>
    <div style="text-align: center; margin-top: 30px; border-top: 1px solid rgba(255,255,255,0.06); padding-top: 20px;">
        <h4 style="color: #bbbbbb; margin-bottom: 20px; text-transform: uppercase; font-size: 14px; letter-spacing: 1px;">Наши производители</h4>
        <div class="elfsight-app-c7586e28-f9a3-4b17-a597-61aeb2b7fe8a" data-elfsight-app-lazy></div>
    </div>
    <div class="container footer-bottom">
        <p>© 2025–2026 Mr. Fix. Все права защищены. «Есть ли у меня план? У меня их три.»</p>
    </div>
</footer>

<button class="ai-agent-toggle" id="aiToggle" title="Спросить Mr. Fix">
    <span class="pulse-ring"></span>
    <svg viewBox="0 0 44 44" xmlns="http://www.w3.org/2000/svg">
        <rect x="8" y="14" width="28" height="22" rx="4" fill="#CC0000"/>
        <rect x="18" y="6" width="8" height="10" rx="2" fill="#CC0000"/>
        <rect x="20" y="4" width="4" height="4" rx="1" fill="#FFCC00"/>
        <circle cx="18" cy="22" r="2" fill="#FFFFFF"/>
        <circle cx="26" cy="22" r="2" fill="#FFFFFF"/>
        <circle cx="18.5" cy="22.5" r="0.8" fill="#1A1E24"/>
        <circle cx="26.5" cy="22.5" r="0.8" fill="#1A1E24"/>
        <path d="M18 28 Q22 31 26 28" stroke="#FFFFFF" stroke-width="1.5" fill="none" stroke-linecap="round"/>
        <rect x="12" y="10" width="20" height="5" rx="2" fill="#FFCC00"/>
    </svg>
</button>

<div class="ai-agent-window" id="aiWindow">
    <div class="ai-agent-header">
        <h4>
            <span class="avatar">
                <svg viewBox="0 0 44 44" xmlns="http://www.w3.org/2000/svg">
                    <rect x="8" y="14" width="28" height="22" rx="4" fill="#CC0000"/>
                    <rect x="18" y="6" width="8" height="10" rx="2" fill="#CC0000"/>
                    <rect x="20" y="4" width="4" height="4" rx="1" fill="#FFCC00"/>
                    <circle cx="18" cy="22" r="2" fill="#FFFFFF"/>
                    <circle cx="26" cy="22" r="2" fill="#FFFFFF"/>
                    <circle cx="18.5" cy="22.5" r="0.8" fill="#1A1E24"/>
                    <circle cx="26.5" cy="22.5" r="0.8" fill="#1A1E24"/>
                    <path d="M18 28 Q22 31 26 28" stroke="#FFFFFF" stroke-width="1.5" fill="none" stroke-linecap="round"/>
                    <rect x="12" y="10" width="20" height="5" rx="2" fill="#FFCC00"/>
                </svg>
            </span>
            Mr. Fix
            <span class="status"><span class="dot"></span> онлайн</span>
        </h4>
        <div style="display:flex; gap:8px;">
            <button id="aiMuteToggle" onclick="toggleMute()" title="Вкл/выкл звук"><i class="fas fa-volume-up"></i></button>
            <button id="aiClose"><i class="fas fa-times"></i></button>
        </div>
    </div>
    <div class="ai-agent-messages" id="aiMessages">
        <div class="ai-msg bot">👋 Здравствуйте! Я Mr. Fix. Есть ли у меня план? У меня их три — герметик, клей, крепёж. Что случилось? Что чиним?</div>
    </div>
    <div class="ai-agent-suggestions" id="aiSuggestions">
        <button class="chip" onclick="aiSendQuick('Чем заделать шов в ванной?')">🧪 Шов в ванной</button>
        <button class="chip" onclick="aiSendQuick('Как повесить полку на гипсокартон?')">🔩 Полка</button>
        <button class="chip" onclick="aiSendQuick('Чем склеить пластик?')">🔧 Пластик</button>
        <button class="chip" onclick="aiSendQuick('Какую клей-пену выбрать?')">💨 Клей-пена</button>
        <button class="chip" onclick="aiSendQuick('Не знаю, что мне нужно')">🤷 Не знаю</button>
    </div>
    <div class="ai-agent-input">
        <input type="text" id="aiInput" placeholder="Опишите задачу..." onkeydown="if(event.key==='Enter') aiSend()">
        <button class="voice-btn" id="aiVoiceBtn" onclick="toggleVoice()"><i class="fas fa-microphone"></i></button>
        <button class="send-btn" onclick="aiSend()"><i class="fas fa-paper-plane"></i></button>
    </div>
</div>

<script>
// ============================================================
// 1. ДАННЫЕ ТОВАРОВ
// ============================================================
const productsData = [
    { id: 1, name: 'Клей-герметик MS-П прозрачный FÖCH 290 мл', sku: 'FL-001', brand: 'FÖCH', category: 'Гибридные клеи', volume: '290 мл', price: 50.87, wholesale: 43.24, stock: true, rating: 4.8, reviews: 45 },
    { id: 2, name: 'Клей-герметик K127 (MS-полимер) FÖCH 290 мл', sku: 'FL-002', brand: 'FÖCH', category: 'Гибридные клеи', volume: '290 мл', price: 84.33, wholesale: 71.68, stock: true, rating: 4.9, reviews: 32 },
    { id: 3, name: 'Клей монтажный Vector (MS-полимер) Tytan Professional 290 мл', sku: 'TYT-003', brand: 'Tytan Professional', category: 'Гибридные клеи', volume: '290 мл', price: 35.00, wholesale: 29.75, stock: true, rating: 4.6, reviews: 28 },
    { id: 4, name: 'Клей-герметик Fix Seal (MS-полимер) Tytan Professional 290 мл', sku: 'TYT-004', brand: 'Tytan Professional', category: 'Гибридные клеи', volume: '290 мл', price: 32.00, wholesale: 27.20, stock: true, rating: 4.7, reviews: 41 },
    { id: 5, name: 'Клей-герметик 2150MS (MS-полимер) Bostik 290 мл', sku: 'BOS-005', brand: 'Bostik', category: 'Гибридные клеи', volume: '290 мл', price: 40.00, wholesale: 34.00, stock: true, rating: 4.7, reviews: 35 },
    { id: 6, name: 'Клей-герметик MS полимер белый Soudal 290 мл', sku: 'SOU-006', brand: 'Soudal', category: 'Гибридные клеи', volume: '290 мл', price: 45.00, wholesale: 38.25, stock: true, rating: 4.8, reviews: 52 },
    { id: 7, name: 'Клей-герметик MS полимер серый Soudal 290 мл', sku: 'SOU-007', brand: 'Soudal', category: 'Гибридные клеи', volume: '290 мл', price: 45.00, wholesale: 38.25, stock: true, rating: 4.8, reviews: 38 },
    { id: 8, name: 'Клей-герметик MS полимер чёрный Soudal 290 мл', sku: 'SOU-008', brand: 'Soudal', category: 'Гибридные клеи', volume: '290 мл', price: 45.00, wholesale: 38.25, stock: true, rating: 4.7, reviews: 29 },
    { id: 9, name: 'Клей-герметик MS полимер белый Ceresit 290 мл', sku: 'CER-009', brand: 'Ceresit', category: 'Гибридные клеи', volume: '290 мл', price: 42.00, wholesale: 35.70, stock: true, rating: 4.7, reviews: 44 },
    { id: 10, name: 'Клей-герметик MS полимер прозрачный Ceresit 290 мл', sku: 'CER-010', brand: 'Ceresit', category: 'Гибридные клеи', volume: '290 мл', price: 42.00, wholesale: 35.70, stock: true, rating: 4.6, reviews: 31 },
    { id: 11, name: 'Клей-герметик MS полимер белый LARGOMIX 290 мл', sku: 'LAR-011', brand: 'LARGOMIX', category: 'Гибридные клеи', volume: '290 мл', price: 38.00, wholesale: 32.30, stock: true, rating: 4.5, reviews: 26 },
    { id: 12, name: 'Клей-герметик MS полимер прозрачный LARGOMIX 290 мл', sku: 'LAR-012', brand: 'LARGOMIX', category: 'Гибридные клеи', volume: '290 мл', price: 38.00, wholesale: 32.30, stock: true, rating: 4.5, reviews: 22 },
    { id: 13, name: 'Клей-герметик MS полимер белый Kiilto 290 мл', sku: 'KII-013', brand: 'Kiilto', category: 'Гибридные клеи', volume: '290 мл', price: 52.00, wholesale: 44.20, stock: true, rating: 4.9, reviews: 48 },
    { id: 14, name: 'Клей-герметик MS полимер прозрачный Kiilto 290 мл', sku: 'KII-014', brand: 'Kiilto', category: 'Гибридные клеи', volume: '290 мл', price: 52.00, wholesale: 44.20, stock: true, rating: 4.9, reviews: 36 },
    { id: 15, name: 'Клей-герметик MS полимер белый Mapei 290 мл', sku: 'MAP-015', brand: 'Mapei', category: 'Гибридные клеи', volume: '290 мл', price: 55.00, wholesale: 46.75, stock: true, rating: 4.9, reviews: 42 },
    { id: 16, name: 'Клей-герметик MS полимер прозрачный Mapei 290 мл', sku: 'MAP-016', brand: 'Mapei', category: 'Гибридные клеи', volume: '290 мл', price: 55.00, wholesale: 46.75, stock: true, rating: 4.9, reviews: 39 },
    { id: 17, name: 'Клей-герметик MS полимер белый Litokol 290 мл', sku: 'LIT-017', brand: 'Litokol', category: 'Гибридные клеи', volume: '290 мл', price: 53.00, wholesale: 45.05, stock: true, rating: 4.8, reviews: 28 },
    { id: 18, name: 'Клей-герметик MS полимер прозрачный Litokol 290 мл', sku: 'LIT-018', brand: 'Litokol', category: 'Гибридные клеи', volume: '290 мл', price: 53.00, wholesale: 45.05, stock: true, rating: 4.8, reviews: 24 },
    { id: 19, name: 'Клей-герметик MS полимер белый Sika 290 мл', sku: 'SIK-019', brand: 'Sika', category: 'Гибридные клеи', volume: '290 мл', price: 58.00, wholesale: 49.30, stock: true, rating: 5.0, reviews: 55 },
    { id: 20, name: 'Клей-герметик MS полимер прозрачный Sika 290 мл', sku: 'SIK-020', brand: 'Sika', category: 'Гибридные клеи', volume: '290 мл', price: 58.00, wholesale: 49.30, stock: true, rating: 5.0, reviews: 47 },
    { id: 21, name: 'Клей-пена полиуретановая Soudal 750 мл', sku: 'SOU-021', brand: 'Soudal', category: 'Полиуретановые клеи', volume: '750 мл', price: 14.25, wholesale: 12.11, stock: true, rating: 4.4, reviews: 67 },
    { id: 22, name: 'Клей-пена полиуретановая Soudal 820 мл', sku: 'SOU-022', brand: 'Soudal', category: 'Полиуретановые клеи', volume: '820 мл', price: 15.19, wholesale: 12.91, stock: true, rating: 4.4, reviews: 54 },
    { id: 23, name: 'Клей-пена полиуретановая Soudal 850 мл', sku: 'SOU-023', brand: 'Soudal', category: 'Полиуретановые клеи', volume: '850 мл', price: 19.82, wholesale: 16.85, stock: true, rating: 4.5, reviews: 61 },
    { id: 24, name: 'Клей-пена полиуретановая Ceresit 750 мл', sku: 'CER-024', brand: 'Ceresit', category: 'Полиуретановые клеи', volume: '750 мл', price: 23.07, wholesale: 19.61, stock: true, rating: 4.6, reviews: 72 },
    { id: 25, name: 'Клей-пена полиуретановая Ceresit 820 мл', sku: 'CER-025', brand: 'Ceresit', category: 'Полиуретановые клеи', volume: '820 мл', price: 16.31, wholesale: 13.86, stock: true, rating: 4.5, reviews: 58 },
    { id: 26, name: 'Клей-пена полиуретановая Ceresit 850 мл', sku: 'CER-026', brand: 'Ceresit', category: 'Полиуретановые клеи', volume: '850 мл', price: 26.20, wholesale: 22.27, stock: true, rating: 4.7, reviews: 65 },
    { id: 27, name: 'Клей-пена полиуретановая LARGOMIX 750 мл', sku: 'LAR-027', brand: 'LARGOMIX', category: 'Полиуретановые клеи', volume: '750 мл', price: 22.69, wholesale: 19.29, stock: true, rating: 4.3, reviews: 42 },
    { id: 28, name: 'Клей-пена полиуретановая LARGOMIX 820 мл', sku: 'LAR-028', brand: 'LARGOMIX', category: 'Полиуретановые клеи', volume: '820 мл', price: 14.66, wholesale: 12.46, stock: true, rating: 4.3, reviews: 38 },
    { id: 29, name: 'Клей-пена полиуретановая LARGOMIX 850 мл', sku: 'LAR-029', brand: 'LARGOMIX', category: 'Полиуретановые клеи', volume: '850 мл', price: 25.66, wholesale: 21.81, stock: true, rating: 4.4, reviews: 45 },
    { id: 30, name: 'Клей-пена полиуретановая Tytan Professional 750 мл', sku: 'TYT-030', brand: 'Tytan Professional', category: 'Полиуретановые клеи', volume: '750 мл', price: 15.49, wholesale: 13.17, stock: true, rating: 4.5, reviews: 81 },
    { id: 31, name: 'Клей-пена полиуретановая Tytan Professional 820 мл', sku: 'TYT-031', brand: 'Tytan Professional', category: 'Полиуретановые клеи', volume: '820 мл', price: 26.07, wholesale: 22.16, stock: true, rating: 4.6, reviews: 62 },
    { id: 32, name: 'Клей-пена полиуретановая Tytan Professional 850 мл', sku: 'TYT-032', brand: 'Tytan Professional', category: 'Полиуретановые клеи', volume: '850 мл', price: 29.87, wholesale: 25.39, stock: true, rating: 4.7, reviews: 55 },
    { id: 33, name: 'Клей-пена полиуретановая Profpur 750 мл', sku: 'PRO-033', brand: 'Profpur', category: 'Полиуретановые клеи', volume: '750 мл', price: 29.99, wholesale: 25.49, stock: true, rating: 4.4, reviews: 33 },
    { id: 34, name: 'Клей-пена полиуретановая Profpur 820 мл', sku: 'PRO-034', brand: 'Profpur', category: 'Полиуретановые клеи', volume: '820 мл', price: 21.09, wholesale: 17.93, stock: true, rating: 4.3, reviews: 29 },
    { id: 35, name: 'Клей-пена полиуретановая Profpur 850 мл', sku: 'PRO-035', brand: 'Profpur', category: 'Полиуретановые клеи', volume: '850 мл', price: 15.62, wholesale: 13.28, stock: true, rating: 4.2, reviews: 26 },
    { id: 36, name: 'Клей-пена полиуретановая Belineco 750 мл', sku: 'BEL-036', brand: 'Belineco', category: 'Полиуретановые клеи', volume: '750 мл', price: 23.37, wholesale: 19.86, stock: true, rating: 4.3, reviews: 31 },
    { id: 37, name: 'Клей-пена полиуретановая Belineco 820 мл', sku: 'BEL-037', brand: 'Belineco', category: 'Полиуретановые клеи', volume: '820 мл', price: 16.35, wholesale: 13.90, stock: true, rating: 4.3, reviews: 27 },
    { id: 38, name: 'Клей-пена полиуретановая Belineco 850 мл', sku: 'BEL-038', brand: 'Belineco', category: 'Полиуретановые клеи', volume: '850 мл', price: 21.39, wholesale: 18.18, stock: true, rating: 4.4, reviews: 34 },
    { id: 39, name: 'Клей-пена полиуретановая WUNDER 750 мл', sku: 'WUN-039', brand: 'WUNDER', category: 'Полиуретановые клеи', volume: '750 мл', price: 26.83, wholesale: 22.81, stock: true, rating: 4.6, reviews: 49 },
    { id: 40, name: 'Клей-пена полиуретановая WUNDER 820 мл', sku: 'WUN-040', brand: 'WUNDER', category: 'Полиуретановые клеи', volume: '820 мл', price: 23.92, wholesale: 20.33, stock: true, rating: 4.6, reviews: 41 },
    { id: 41, name: 'Клей-пена полиуретановая WUNDER 850 мл', sku: 'WUN-041', brand: 'WUNDER', category: 'Полиуретановые клеи', volume: '850 мл', price: 26.93, wholesale: 22.89, stock: true, rating: 4.7, reviews: 46 },
    { id: 42, name: 'Клей-пена полиуретановая Kudo 750 мл', sku: 'KUD-042', brand: 'Kudo', category: 'Полиуретановые клеи', volume: '750 мл', price: 15.90, wholesale: 13.52, stock: true, rating: 4.4, reviews: 37 },
    { id: 43, name: 'Клей-пена полиуретановая Kudo 820 мл', sku: 'KUD-043', brand: 'Kudo', category: 'Полиуретановые клеи', volume: '820 мл', price: 29.99, wholesale: 25.49, stock: true, rating: 4.5, reviews: 42 },
    { id: 44, name: 'Клей-пена полиуретановая Kudo 850 мл', sku: 'KUD-044', brand: 'Kudo', category: 'Полиуретановые клеи', volume: '850 мл', price: 20.33, wholesale: 17.28, stock: true, rating: 4.4, reviews: 35 },
    { id: 45, name: 'Клей-пена полиуретановая Penosil 750 мл', sku: 'PEN-045', brand: 'Penosil', category: 'Полиуретановые клеи', volume: '750 мл', price: 20.07, wholesale: 17.06, stock: true, rating: 4.7, reviews: 58 },
    { id: 46, name: 'Клей-пена полиуретановая Penosil 820 мл', sku: 'PEN-046', brand: 'Penosil', category: 'Полиуретановые клеи', volume: '820 мл', price: 25.11, wholesale: 21.34, stock: true, rating: 4.7, reviews: 47 },
    { id: 47, name: 'Клей-пена полиуретановая Penosil 850 мл', sku: 'PEN-047', brand: 'Penosil', category: 'Полиуретановые клеи', volume: '850 мл', price: 28.70, wholesale: 24.40, stock: true, rating: 4.8, reviews: 52 },
    { id: 48, name: 'Клей-пена полиуретановая Mastersil 750 мл', sku: 'MAS-048', brand: 'Mastersil', category: 'Полиуретановые клеи', volume: '750 мл', price: 19.26, wholesale: 16.37, stock: true, rating: 4.5, reviews: 39 },
    { id: 49, name: 'Клей-пена полиуретановая Mastersil 820 мл', sku: 'MAS-049', brand: 'Mastersil', category: 'Полиуретановые клеи', volume: '820 мл', price: 29.93, wholesale: 25.44, stock: true, rating: 4.6, reviews: 44 },
    { id: 50, name: 'Клей-пена полиуретановая Mastersil 850 мл', sku: 'MAS-050', brand: 'Mastersil', category: 'Полиуретановые клеи', volume: '850 мл', price: 27.65, wholesale: 23.50, stock: true, rating: 4.6, reviews: 41 },
    { id: 51, name: 'Герметик силиконовый санитарный белый Soudal 280 мл', sku: 'SOU-051', brand: 'Soudal', category: 'Силиконовые герметики', volume: '280 мл', price: 22.08, wholesale: 18.77, stock: true, rating: 4.7, reviews: 89 },
    { id: 52, name: 'Герметик силиконовый санитарный прозрачный Soudal 280 мл', sku: 'SOU-052', brand: 'Soudal', category: 'Силиконовые герметики', volume: '280 мл', price: 19.48, wholesale: 16.56, stock: true, rating: 4.7, reviews: 76 },
    { id: 53, name: 'Герметик силиконовый нейтральный белый Soudal 280 мл', sku: 'SOU-053', brand: 'Soudal', category: 'Силиконовые герметики', volume: '280 мл', price: 17.86, wholesale: 15.18, stock: true, rating: 4.6, reviews: 63 },
    { id: 54, name: 'Герметик силиконовый нейтральный прозрачный Soudal 280 мл', sku: 'SOU-054', brand: 'Soudal', category: 'Силиконовые герметики', volume: '280 мл', price: 16.82, wholesale: 14.30, stock: true, rating: 4.6, reviews: 58 },
    { id: 55, name: 'Герметик силиконовый санитарный белый Ceresit 280 мл', sku: 'CER-055', brand: 'Ceresit', category: 'Силиконовые герметики', volume: '280 мл', price: 18.06, wholesale: 15.35, stock: true, rating: 4.6, reviews: 72 },
    { id: 56, name: 'Герметик силиконовый санитарный прозрачный Ceresit 280 мл', sku: 'CER-056', brand: 'Ceresit', category: 'Силиконовые герметики', volume: '280 мл', price: 23.15, wholesale: 19.68, stock: true, rating: 4.7, reviews: 65 },
    { id: 57, name: 'Герметик силиконовый нейтральный белый Ceresit 280 мл', sku: 'CER-057', brand: 'Ceresit', category: 'Силиконовые герметики', volume: '280 мл', price: 15.29, wholesale: 13.00, stock: true, rating: 4.5, reviews: 54 },
    { id: 58, name: 'Герметик силиконовый нейтральный прозрачный Ceresit 280 мл', sku: 'CER-058', brand: 'Ceresit', category: 'Силиконовые герметики', volume: '280 мл', price: 10.42, wholesale: 8.86, stock: true, rating: 4.5, reviews: 61 },
    { id: 59, name: 'Герметик силиконовый санитарный белый LARGOMIX 280 мл', sku: 'LAR-059', brand: 'LARGOMIX', category: 'Силиконовые герметики', volume: '280 мл', price: 10.29, wholesale: 8.75, stock: true, rating: 4.3, reviews: 48 },
    { id: 60, name: 'Герметик силиконовый санитарный прозрачный LARGOMIX 280 мл', sku: 'LAR-060', brand: 'LARGOMIX', category: 'Силиконовые герметики', volume: '280 мл', price: 17.99, wholesale: 15.29, stock: true, rating: 4.4, reviews: 42 },
    { id: 61, name: 'Герметик силиконовый нейтральный белый LARGOMIX 280 мл', sku: 'LAR-061', brand: 'LARGOMIX', category: 'Силиконовые герметики', volume: '280 мл', price: 20.91, wholesale: 17.77, stock: true, rating: 4.4, reviews: 36 },
    { id: 62, name: 'Герметик силиконовый нейтральный прозрачный LARGOMIX 280 мл', sku: 'LAR-062', brand: 'LARGOMIX', category: 'Силиконовые герметики', volume: '280 мл', price: 19.80, wholesale: 16.83, stock: true, rating: 4.4, reviews: 33 },
    { id: 63, name: 'Герметик силиконовый санитарный белый Tytan Professional 280 мл', sku: 'TYT-063', brand: 'Tytan Professional', category: 'Силиконовые герметики', volume: '280 мл', price: 20.10, wholesale: 17.09, stock: true, rating: 4.6, reviews: 57 },
    { id: 64, name: 'Герметик силиконовый санитарный прозрачный Tytan Professional 280 мл', sku: 'TYT-064', brand: 'Tytan Professional', category: 'Силиконовые герметики', volume: '280 мл', price: 22.84, wholesale: 19.41, stock: true, rating: 4.6, reviews: 51 },
    { id: 65, name: 'Герметик силиконовый нейтральный белый Tytan Professional 280 мл', sku: 'TYT-065', brand: 'Tytan Professional', category: 'Силиконовые герметики', volume: '280 мл', price: 15.80, wholesale: 13.43, stock: true, rating: 4.5, reviews: 44 },
    { id: 66, name: 'Герметик силиконовый нейтральный прозрачный Tytan Professional 280 мл', sku: 'TYT-066', brand: 'Tytan Professional', category: 'Силиконовые герметики', volume: '280 мл', price: 14.00, wholesale: 11.90, stock: true, rating: 4.5, reviews: 39 },
    { id: 67, name: 'Герметик силиконовый санитарный белый Bostik 280 мл', sku: 'BOS-067', brand: 'Bostik', category: 'Силиконовые герметики', volume: '280 мл', price: 17.39, wholesale: 14.78, stock: true, rating: 4.5, reviews: 46 },
    { id: 68, name: 'Герметик силиконовый санитарный прозрачный Bostik 280 мл', sku: 'BOS-068', brand: 'Bostik', category: 'Силиконовые герметики', volume: '280 мл', price: 9.67, wholesale: 8.22, stock: true, rating: 4.4, reviews: 52 },
    { id: 69, name: 'Герметик силиконовый нейтральный белый Bostik 280 мл', sku: 'BOS-069', brand: 'Bostik', category: 'Силиконовые герметики', volume: '280 мл', price: 17.86, wholesale: 15.18, stock: true, rating: 4.5, reviews: 38 },
    { id: 70, name: 'Герметик силиконовый нейтральный прозрачный Bostik 280 мл', sku: 'BOS-070', brand: 'Bostik', category: 'Силиконовые герметики', volume: '280 мл', price: 16.17, wholesale: 13.74, stock: true, rating: 4.5, reviews: 41 },
    { id: 159, name: 'Герметик акриловый белый LARGOMIX 280 мл', sku: 'LAR-159', brand: 'LARGOMIX', category: 'Акриловые герметики', volume: '280 мл', price: 10.63, wholesale: 9.04, stock: true, rating: 4.4, reviews: 37 },
    { id: 160, name: 'Герметик акриловый бежевый LARGOMIX 280 мл', sku: 'LAR-160', brand: 'LARGOMIX', category: 'Акриловые герметики', volume: '280 мл', price: 14.18, wholesale: 12.05, stock: true, rating: 4.4, reviews: 29 },
    { id: 161, name: 'Герметик акриловый серый LARGOMIX 280 мл', sku: 'LAR-161', brand: 'LARGOMIX', category: 'Акриловые герметики', volume: '280 мл', price: 12.30, wholesale: 10.46, stock: true, rating: 4.4, reviews: 26 },
    { id: 162, name: 'Герметик акриловый белый Soudal 280 мл', sku: 'SOU-162', brand: 'Soudal', category: 'Акриловые герметики', volume: '280 мл', price: 8.44, wholesale: 7.17, stock: true, rating: 4.6, reviews: 68 },
    { id: 163, name: 'Герметик акриловый бежевый Soudal 280 мл', sku: 'SOU-163', brand: 'Soudal', category: 'Акриловые герметики', volume: '280 мл', price: 6.87, wholesale: 5.84, stock: true, rating: 4.5, reviews: 42 },
    { id: 164, name: 'Герметик акриловый серый Soudal 280 мл', sku: 'SOU-164', brand: 'Soudal', category: 'Акриловые герметики', volume: '280 мл', price: 8.06, wholesale: 6.85, stock: true, rating: 4.5, reviews: 35 },
    { id: 165, name: 'Герметик акриловый белый Ceresit 280 мл', sku: 'CER-165', brand: 'Ceresit', category: 'Акриловые герметики', volume: '280 мл', price: 9.47, wholesale: 8.05, stock: true, rating: 4.5, reviews: 57 },
    { id: 166, name: 'Герметик акриловый бежевый Ceresit 280 мл', sku: 'CER-166', brand: 'Ceresit', category: 'Акриловые герметики', volume: '280 мл', price: 9.62, wholesale: 8.18, stock: true, rating: 4.5, reviews: 39 },
    { id: 167, name: 'Герметик акриловый серый Ceresit 280 мл', sku: 'CER-167', brand: 'Ceresit', category: 'Акриловые герметики', volume: '280 мл', price: 10.80, wholesale: 9.18, stock: true, rating: 4.6, reviews: 33 },
    { id: 234, name: 'Фуга эпоксидная Mapei 1 кг', sku: 'MAP-234', brand: 'Mapei', category: 'Эпоксидные затирки', volume: '1 кг', price: 83.13, wholesale: 70.66, stock: true, rating: 4.9, reviews: 88 },
    { id: 235, name: 'Фуга эпоксидная Mapei 2 кг', sku: 'MAP-235', brand: 'Mapei', category: 'Эпоксидные затирки', volume: '2 кг', price: 155.04, wholesale: 131.78, stock: true, rating: 4.9, reviews: 62 },
    { id: 236, name: 'Фуга эпоксидная Mapei 2.5 кг', sku: 'MAP-236', brand: 'Mapei', category: 'Эпоксидные затирки', volume: '2.5 кг', price: 255.79, wholesale: 217.42, stock: true, rating: 4.8, reviews: 41 },
    { id: 237, name: 'Фуга эпоксидная Mapei 3 кг', sku: 'MAP-237', brand: 'Mapei', category: 'Эпоксидные затирки', volume: '3 кг', price: 225.22, wholesale: 191.44, stock: true, rating: 4.8, reviews: 33 },
    { id: 238, name: 'Фуга эпоксидная Mapei 3.5 кг', sku: 'MAP-238', brand: 'Mapei', category: 'Эпоксидные затирки', volume: '3.5 кг', price: 255.77, wholesale: 217.40, stock: true, rating: 4.8, reviews: 28 },
    { id: 239, name: 'Фуга эпоксидная Mapei 5 кг', sku: 'MAP-239', brand: 'Mapei', category: 'Эпоксидные затирки', volume: '5 кг', price: 92.84, wholesale: 78.91, stock: true, rating: 4.7, reviews: 22 },
    { id: 240, name: 'Фуга эпоксидная Litokol 1 кг', sku: 'LIT-240', brand: 'Litokol', category: 'Эпоксидные затирки', volume: '1 кг', price: 154.41, wholesale: 131.25, stock: true, rating: 4.9, reviews: 54 },
    { id: 241, name: 'Фуга эпоксидная Litokol 2 кг', sku: 'LIT-241', brand: 'Litokol', category: 'Эпоксидные затирки', volume: '2 кг', price: 233.46, wholesale: 198.44, stock: true, rating: 4.9, reviews: 38 },
    { id: 242, name: 'Фуга эпоксидная Litokol 2.5 кг', sku: 'LIT-242', brand: 'Litokol', category: 'Эпоксидные затирки', volume: '2.5 кг', price: 152.29, wholesale: 129.45, stock: true, rating: 4.8, reviews: 31 },
    { id: 243, name: 'Фуга эпоксидная Litokol 3 кг', sku: 'LIT-243', brand: 'Litokol', category: 'Эпоксидные затирки', volume: '3 кг', price: 276.44, wholesale: 234.97, stock: true, rating: 4.8, reviews: 26 },
    { id: 424, name: 'Респиратор ffp1 CCK', sku: 'CCK-424', brand: 'CCK', category: 'СИЗ', volume: '1 шт', price: 4.72, wholesale: 4.01, stock: true, rating: 4.5, reviews: 56 },
    { id: 425, name: 'Респиратор ffp1 Robinzon', sku: 'ROB-425', brand: 'Robinzon', category: 'СИЗ', volume: '1 шт', price: 25.12, wholesale: 21.35, stock: true, rating: 4.7, reviews: 42 },
    { id: 426, name: 'Респиратор ffp1 Stroimhatu', sku: 'STR-426', brand: 'Stroimhatu', category: 'СИЗ', volume: '1 шт', price: 6.33, wholesale: 5.38, stock: true, rating: 4.4, reviews: 38 },
    { id: 427, name: 'Респиратор ffp1 Specovka', sku: 'SPE-427', brand: 'Specovka', category: 'СИЗ', volume: '1 шт', price: 16.02, wholesale: 13.62, stock: true, rating: 4.5, reviews: 33 },
    { id: 428, name: 'Респиратор ffp1 Europrotect', sku: 'EUR-428', brand: 'Europrotect', category: 'СИЗ', volume: '1 шт', price: 23.28, wholesale: 19.79, stock: true, rating: 4.7, reviews: 47 },
    { id: 404, name: 'Перчатки нитриловые одноразовые MY1230', sku: 'MY-404', brand: 'MY1230', category: 'СИЗ', volume: '1 уп', price: 14.97, wholesale: 12.72, stock: true, rating: 4.5, reviews: 62 },
    { id: 405, name: 'Перчатки нитриловые многоразовые MY1230', sku: 'MY-405', brand: 'MY1230', category: 'СИЗ', volume: '1 уп', price: 11.65, wholesale: 9.90, stock: true, rating: 4.4, reviews: 45 },
    { id: 406, name: 'Перчатки нитриловые одноразовые Europrotect', sku: 'EUR-406', brand: 'Europrotect', category: 'СИЗ', volume: '1 уп', price: 16.76, wholesale: 14.25, stock: true, rating: 4.4, reviews: 52 },
    { id: 407, name: 'Перчатки нитриловые многоразовые Europrotect', sku: 'EUR-407', brand: 'Europrotect', category: 'СИЗ', volume: '1 уп', price: 18.15, wholesale: 15.43, stock: true, rating: 4.6, reviews: 48 },
    { id: 408, name: 'Перчатки нитриловые одноразовые Dilins', sku: 'DIL-408', brand: 'Dilins', category: 'СИЗ', volume: '1 уп', price: 2.92, wholesale: 2.48, stock: true, rating: 4.3, reviews: 78 },
    { id: 409, name: 'Перчатки нитриловые многоразовые Dilins', sku: 'DIL-409', brand: 'Dilins', category: 'СИЗ', volume: '1 уп', price: 3.65, wholesale: 3.10, stock: true, rating: 4.4, reviews: 56 },
];

const defaultImage = 'https://avatars.mds.yandex.net/get-mpic/19767307/2a0000019f4961664dbbd5dc9687639d7ef6/orig';
const categories = [...new Set(productsData.map(p => p.category))];

const libraryItems = [
    { icon: '📘', title: 'Как выбрать герметик: силикон vs акрил vs MS', description: 'Разбираемся раз и навсегда', type: 'Статья', tags: ['Герметики'], date: '15.05.2025' },
    { icon: '📋', title: 'Клей-пена: как правильно наносить', description: 'Инструкция для новичка', type: 'Статья', tags: ['Клеи'], date: '02.06.2025' },
    { icon: '🎥', title: 'Эпоксидная затирка: видеоурок', description: 'Пошагово для санузла и кухни', type: 'Видео', tags: ['Затирки'], date: '20.04.2025' },
    { icon: '📘', title: 'СИЗ: что выбрать для покраски', description: 'Респираторы и перчатки', type: 'Статья', tags: ['СИЗ'], date: '10.05.2025' },
    { icon: '📋', title: '10 ошибок при работе с герметиком', description: 'И как их избежать', type: 'Статья', tags: ['Герметики'], date: '28.04.2025' },
    { icon: '🎥', title: 'Как выбрать крепёж для гипсокартона', description: 'Driva, Molly или профиль?', type: 'Видео', tags: ['Крепёж'], date: '15.03.2025' },
];

// ============================================================
// 2. РЕНДЕР
// ============================================================
function renderCatalog() {
    const grid = document.getElementById('catalogGrid');
    const sample = productsData.slice(0, 8);
    grid.innerHTML = sample.map(p => {
        const stars = '★'.repeat(Math.floor(p.rating)) + '☆'.repeat(5 - Math.floor(p.rating));
        return `
            <div class="product-card reveal">
                <div class="product-card__image">
                    <img src="${defaultImage}" alt="${p.name}" onerror="this.src='${defaultImage}'">
                    ${p.rating >= 4.8 ? '<span class="product-card__badge">ХИТ</span>' : ''}
                </div>
                <div class="product-card__sku">${p.sku} • ${p.brand}</div>
                <div class="product-card__title">${p.name}</div>
                <div class="product-card__rating">
                    <span class="product-card__stars">${stars}</span>
                    <span class="product-card__reviews">(${p.reviews})</span>
                </div>
                <div class="product-card__price">
                    <span class="product-card__price-current">${p.price.toFixed(2)} BYN</span>
                    <span class="product-card__price-wholesale">Опт: ${p.wholesale.toFixed(2)} BYN</span>
                </div>
                <div class="product-card__stock ${p.stock ? 'product-card__stock--in' : 'product-card__stock--order'}">
                    ${p.stock ? '✓ В наличии' : '⏳ Под заказ'}
                </div>
                <div class="product-card__actions">
                    <button class="btn btn-primary btn-sm" onclick="addToCart(${p.id})"><i class="fas fa-cart-plus"></i> В корзину</button>
                    <button class="btn btn--tech btn-sm" onclick="showNotification('📄 Техническая информация по ${p.name}')"><i class="fas fa-info-circle"></i></button>
                </div>
            </div>
        `;
    }).join('');
}

let cartItems = [];
function addToCart(id) {
    const product = productsData.find(p => p.id === id);
    if (product) {
        cartItems.push(product);
        updateCartCount();
        showNotification(`✅ ${product.name} добавлен в корзину`);
        speakText(`${product.name} добавлен в корзину`);
    }
}
function updateCartCount() {
    const countEl = document.getElementById('cartCount');
    countEl.style.display = cartItems.length > 0 ? 'flex' : 'none';
    countEl.textContent = cartItems.length;
}

let filteredPriceData = [...productsData];
function renderPriceAccordion(data) {
    const container = document.getElementById('priceAccordion');
    const grouped = {};
    data.forEach(p => {
        if (!grouped[p.category]) grouped[p.category] = [];
        grouped[p.category].push(p);
    });
    let html = '';
    Object.keys(grouped).forEach(cat => {
        const items = grouped[cat];
        html += `
            <div class="price-category">
                <div class="price-category-header" onclick="toggleCategory(this)">
                    <span class="cat-title"><span class="icon">📂</span> ${cat} <span class="cat-count">${items.length}</span></span>
                    <span class="arrow"><i class="fas fa-chevron-down"></i></span>
                </div>
                <div class="price-category-body">
                    <table class="price-table">
                        <thead><tr><th style="min-width:180px;">Товар</th><th>Бренд</th><th>Фасовка</th><th>Цена розн.</th><th>Цена опт.</th><th>Наличие</th></tr></thead>
                        <tbody>
                            ${items.map(p => `
                                <tr>
                                    <td><div class="product-cell"><div class="name">${p.name}</div><div class="sku">${p.sku}</div></div></td>
                                    <td><span class="brand-tag">${p.brand}</span></td>
                                    <td>${p.volume}</td>
                                    <td class="price-current">${p.price.toFixed(2)} BYN</td>
                                    <td class="price-wholesale">${p.wholesale.toFixed(2)} BYN</td>
                                    <td><span class="${p.stock ? 'stock-in' : 'stock-order'}">${p.stock ? '✓' : '⏳'}</span></td>
                                </tr>
                            `).join('')}
                        </tbody>
                    </table>
                </div>
            </div>
        `;
    });
    container.innerHTML = html;
    document.getElementById('rowCount').textContent = `Показано: ${data.length}`;
}

function toggleCategory(header) {
    const body = header.nextElementSibling;
    const isOpen = body.classList.contains('open');
    document.querySelectorAll('.price-category-body').forEach(el => el.classList.remove('open'));
    document.querySelectorAll('.price-category-header').forEach(el => el.classList.remove('open'));
    if (!isOpen) {
        body.classList.add('open');
        header.classList.add('open');
    }
}

function filterPrice() {
    const search = document.getElementById('searchInput').value.toLowerCase();
    const category = document.getElementById('categoryFilter').value;
    filteredPriceData = productsData.filter(p => {
        const matchSearch = p.name.toLowerCase().includes(search) || p.sku.toLowerCase().includes(search) || p.brand.toLowerCase().includes(search);
        const matchCategory = category === 'all' || p.category === category;
        return matchSearch && matchCategory;
    });
    renderPriceAccordion(filteredPriceData);
}

function populateFilters() {
    const catSelect = document.getElementById('categoryFilter');
    categories.forEach(c => {
        const opt = document.createElement('option');
        opt.value = c;
        opt.textContent = c;
        catSelect.appendChild(opt);
    });
    document.getElementById('priceBadge').textContent = `${productsData.length} товаров`;
}

function exportCSV() {
    const headers = ['ID', 'Наименование', 'Артикул', 'Бренд', 'Категория', 'Фасовка', 'Цена розн.', 'Цена опт.', 'Наличие'];
    const rows = productsData.map(p => [p.id, p.name, p.sku, p.brand, p.category, p.volume, p.price.toFixed(2), p.wholesale.toFixed(2), p.stock ? 'В наличии' : 'Под заказ']);
    const csv = [headers.join(';'), ...rows.map(r => r.join(';'))].join('\n');
    const blob = new Blob(['\uFEFF' + csv], { type: 'text/csv;charset=utf-8;' });
    const link = document.createElement('a');
    link.href = URL.createObjectURL(blob);
    link.download = 'mrfx_pricelist.csv';
    link.click();
    showNotification('✅ CSV скачан');
}

function renderLibrary() {
    const grid = document.getElementById('libraryGrid');
    grid.innerHTML = libraryItems.map(item => `
        <div class="library-card reveal" onclick="showNotification('📄 Открывается: ${item.title}')">
            <span class="icon">${item.icon}</span>
            <h3>${item.title}</h3>
            <p>${item.description}</p>
            <div class="meta"><span class="tag-sm">${item.type}</span><span>${item.date}</span></div>
        </div>
    `).join('');
}

function renderReviews() {
    const grid = document.getElementById('reviewsGrid');
    const reviewsData = [
        { name: 'Александр Петров', rating: 5, text: 'Mr. Fix сначала пошутил, потом задал три вопроса и выдал точный герметик. Soudal санитарный держится уже 2 года!', product: 'Soudal санитарный', date: '15.03.2025' },
        { name: 'Екатерина Смирнова', rating: 5, text: 'Спросила про полку — бот пошутил про «сломать», а потом дал точный совет. Купила крепёж, всё висит!', product: 'Крепёж для ГКЛ', date: '22.02.2025' },
        { name: 'Иван Козлов', rating: 4, text: 'Отличный подход: юмор в начале, серьёзный подбор в конце. Клей-пена Soudal 750 мл — работает отлично.', product: 'Soudal клей-пена', date: '10.01.2025' }
    ];
    grid.innerHTML = reviewsData.map(r => {
        const stars = '★'.repeat(r.rating) + '☆'.repeat(5 - r.rating);
        return `
            <div class="review-card reveal">
                <div class="review-header"><span class="name">${r.name}</span><span class="date">${r.date}</span></div>
                <div class="review-stars">${stars}</div>
                <div class="review-text">${r.text}</div>
                <div class="review-product">📦 ${r.product}</div>
            </div>
        `;
    }).join('');
}

function filterDocs(type, btn) {
    const cards = document.querySelectorAll('.doc-card');
    cards.forEach(card => {
        if (type === 'all' || card.dataset.type === type) {
            card.style.display = 'flex';
        } else {
            card.style.display = 'none';
        }
    });
    document.querySelectorAll('.doc-tab').forEach(tab => tab.classList.remove('active'));
    btn.classList.add('active');
}

function searchCatalog() {
    const query = document.getElementById('smart-search-input').value.trim().toLowerCase();
    document.getElementById('searchInput').value = query;
    filterPrice();
    document.getElementById('price').scrollIntoView({ behavior: 'smooth' });
    showNotification(`🔍 Найдено ${filteredPriceData.length} товаров`);
}
function searchTag(tag) {
    document.getElementById('smart-search-input').value = tag;
    searchCatalog();
}

function submitB2B(e) {
    e.preventDefault();
    const name = document.getElementById('b2bName').value;
    const company = document.getElementById('b2bCompany').value;
    showNotification(`✅ Запрос от ${name} (${company}) отправлен!`);
    e.target.reset();
}

// ============================================================
// ИИ-АГЕНТ
// ============================================================
const aiToggle = document.getElementById('aiToggle');
const aiWindow = document.getElementById('aiWindow');
const aiClose = document.getElementById('aiClose');
const aiMuteToggle = document.getElementById('aiMuteToggle');
const aiInput = document.getElementById('aiInput');
const aiMessages = document.getElementById('aiMessages');
const aiVoiceBtn = document.getElementById('aiVoiceBtn');

let isMuted = false;
let isVoiceListening = false;
let recognition = null;
let speechSynth = window.speechSynthesis;

function speakText(text) {
    if (isMuted) return;
    if (speechSynth.speaking) speechSynth.cancel();
    const utterance = new SpeechSynthesisUtterance(text);
    utterance.lang = 'ru-RU';
    utterance.rate = 0.95;
    utterance.pitch = 1.05;
    speechSynth.speak(utterance);
}

function toggleMute() {
    isMuted = !isMuted;
    if (isMuted) {
        aiMuteToggle.innerHTML = '<i class="fas fa-volume-mute"></i>';
        if (speechSynth.speaking) speechSynth.cancel();
        showNotification('🔇 Звук выключен');
    } else {
        aiMuteToggle.innerHTML = '<i class="fas fa-volume-up"></i>';
        showNotification('🔊 Звук включен');
    }
}

aiToggle.addEventListener('click', () => {
    aiWindow.classList.toggle('open');
    if (aiWindow.classList.contains('open')) aiInput.focus();
});
aiClose.addEventListener('click', () => aiWindow.classList.remove('open'));

function aiSend() {
    const text = aiInput.value.trim();
    if (!text) return;
    addMessage(text, 'user');
    aiInput.value = '';
    processAI(text);
}
function aiSendQuick(text) {
    addMessage(text, 'user');
    processAI(text);
}
function addMessage(text, type) {
    const msg = document.createElement('div');
    msg.className = `ai-msg ${type}`;
    msg.textContent = text;
    aiMessages.appendChild(msg);
    aiMessages.scrollTop = aiMessages.scrollHeight;
}

function processAI(query) {
    const typingMsg = document.createElement('div');
    typingMsg.className = 'ai-msg bot';
    typingMsg.innerHTML = '<span class="typing">...</span>';
    aiMessages.appendChild(typingMsg);
    aiMessages.scrollTop = aiMessages.scrollHeight;

    setTimeout(() => {
        typingMsg.remove();
        const reply = generateFixReply(query.toLowerCase());
        addMessage(reply, 'bot');
        aiMessages.scrollTop = aiMessages.scrollHeight;
        speakText(reply);
    }, 600 + Math.random() * 400);
}

// ============================================================
// 72 СЦЕНАРИЯ MR. FIX
// ============================================================
function generateFixReply(q) {
    if (q.includes('привет') || q.includes('здравствуй')) {
        return '👋 Здравствуйте! Mr. Fix на связи. Есть ли у меня план? У меня их три. Рассказывайте: что сломалось, отвалилось, течёт или скрипит?';
    }

    // MS-ПОЛИМЕРЫ
    if (q.includes('ms') || q.includes('гибридн') || q.includes('полимер')) {
        if (q.includes('ванн') || q.includes('кухн') || q.includes('влажн')) {
            return 'MS-полимер во влажной зоне? Отличный выбор. Не боится воды, не темнеет.\n\n• Бюджет — Tytan Fix Seal, 32 BYN\n• Оптимум — Soudal MS белый, 45 BYN\n• Премиум — Mapei MS прозрачный, 55 BYN\n\n📖 Подробнее: «MS-полимеры: универсальный солдат» — в Библиотеке.';
        }
        if (q.includes('дерев') || q.includes('мебел')) {
            return 'MS-полимер для дерева? Работает.\n\n• Мебель внутри — Soudal MS белый, 45 BYN\n• Терраса, фасад — Sika MS, 58 BYN\n• Максимальная прочность — эпоксид\n\n📖 Подробнее — в Библиотеке.';
        }
        if (q.includes('металл')) {
            return 'MS-полимер для металла? Держит.\n\n• Лёгкая нагрузка — Bostik 2150MS, 40 BYN\n• Средняя — Soudal MS, 45 BYN\n• Тяжёлая — эпоксид\n\nСовет: металл обезжирить.';
        }
        if (q.includes('пластик')) {
            return 'MS-полимер для пластика? Работает с большинством.\n\n• Универсально — Tytan Vector, 35 BYN\n• Премиум — Kiilto MS, 52 BYN\n• Если не держит — эпоксид\n\nСовет: полипропилен и полиэтилен плохо клеятся.';
        }
        if (q.includes('камен') || q.includes('мрамор')) {
            return 'MS-полимер для камня? Отлично.\n\n• Бюджет — Ceresit MS, 42 BYN\n• Оптимум — Soudal MS, 45 BYN\n• Премиум — Mapei MS, 55 BYN\n\nСовет: для мрамора берите белый.';
        }
        if (q.includes('зеркал') || q.includes('стекл')) {
            return 'MS-полимер для зеркала? Можно, но осторожно.\n\n• Крепление — MS + дюбель\n• Герметизация — Soudal MS прозрачный, 45 BYN\n• Большое зеркало — только крепёж\n\nСовет: не клейте зеркало только на клей.';
        }
        if (q.includes('фасад') || q.includes('улиц')) {
            return 'MS-полимер для фасада? Да, если влагостойкий.\n\n• Sika MS, 58 BYN — влагостойкий\n• Mapei MS, 55 BYN — премиум\n• Kiilto MS, 52 BYN — финское качество\n\nСовет: для фасада — нейтральный.';
        }
        if (q.includes('авто') || q.includes('машин')) {
            return 'MS-полимер для авто? Есть специальные составы.\n\n• Для кузова — Sika MS, 58 BYN\n• Для салона — Soudal MS, 45 BYN\n• Для стёкол — специальный клей\n\nСовет: для авто лучше полиуретан.';
        }
        if (q.includes('какой') && q.includes('лучше')) {
            return 'Какой MS-полимер лучше? По бюджету:\n\n• До 35 BYN — Tytan Fix Seal, Vector\n• 38–42 BYN — LARGOMIX, Ceresit, Bostik\n• 45–52 BYN — Soudal, Kiilto\n• 55–58 BYN — Mapei, Sika, Litokol\n\nЧестно: разница не критична.';
        }
        return 'MS-полимеры! Универсальные солдаты. Клеят почти всё.\n\nУточним:\n1. Что склеиваем — дерево, металл, пластик, камень?\n2. Внутри или снаружи?\n3. Влажно или сухо?\n\nПлан: MS подходит для 90% задач.';
    }

    // КЛЕЙ-ПЕНА
    if (q.includes('клей-пен') || q.includes('клей пена') || (q.includes('пен') && q.includes('клей'))) {
        if (q.includes('пенопласт') || q.includes('утеплит')) {
            return 'Клей-пена для пенопласта? Её хлеб.\n\n• Бюджет — Soudal 750 мл, 14.25 BYN\n• Оптимум — Ceresit 750 мл, 23.07 BYN\n• Профи — Penosil 850 мл, 28.70 BYN\n\nСовет: для улицы — влагостойкую.';
        }
        if (q.includes('гипсокартон') || q.includes('гкл')) {
            return 'Клей-пена для гипсокартона? Отлично.\n\n• Бюджет — Soudal 750 мл, 14.25 BYN\n• Оптимум — Tytan 750 мл, 15.49 BYN\n• Профи — Penosil 850 мл, 28.70 BYN\n\nСовет: наносите змейкой.';
        }
        if (q.includes('кирпич') || q.includes('блок') || q.includes('газобетон')) {
            return 'Клей-пена для кирпича и блоков? Работает.\n\n• Бюджет — Soudal 750 мл, 14.25 BYN\n• Оптимум — Ceresit 850 мл, 26.20 BYN\n• Профи — Penosil 850 мл, 28.70 BYN\n\nСовет: поверхность увлажнить.';
        }
        if (q.includes('дерев') || q.includes('брус')) {
            return 'Клей-пена для дерева? Осторожно.\n\n• Для террас — Penosil 850 мл, 28.70 BYN\n• Для мебели — ПВА или MS\n• Для несущих — только крепёж\n\nСовет: пена расширяется.';
        }
        if (q.includes('зим') || q.includes('мороз') || q.includes('холод')) {
            return 'Зимняя клей-пена! Тут всё серьёзно.\n\n• Бюджет — Soudal зимняя, 14.25 BYN\n• Оптимум — Penosil зимняя, 28.70 BYN\n• Профи — Tytan зимняя, 29.87 BYN\n\nСовет: обычная пена при −10°C не работает.';
        }
        if (q.includes('какой') && q.includes('лучше')) {
            return 'Какая клей-пена лучше?\n\n• До 15 BYN — Soudal, LARGOMIX\n• 15–25 BYN — Ceresit, Tytan, Belineco, Kudo\n• 25–30 BYN — Penosil, WUNDER, Mastersil\n\nЧестно: для быта хватит бюджетной.';
        }
        if (q.includes('сколько') || q.includes('расход')) {
            return 'Сколько пены нужно?\n\n• 1 баллон 750 мл = ~10–12 м шва\n• 1 баллон 850 мл = ~12–15 м шва\n• Окно = 1–1.5 баллона\n• Дверь = 1.5–2 баллона\n• Стена 10 м² = 2–3 баллона\n\nСовет: берите с запасом.';
        }
        return 'Клей-пена! Универсальный солдат.\n\nУточним:\n1. Что клеим — пенопласт, ГКЛ, кирпич, дерево?\n2. Внутри или снаружи?\n3. Нужна ли теплоизоляция?\n\n• Бюджет — Soudal 750 мл, 14.25 BYN\n• Оптимум — Tytan 750 мл, 15.49 BYN\n• Премиум — Penosil 850 мл, 28.70 BYN';
    }

    // СИЛИКОН
    if (q.includes('силикон')) {
        if (q.includes('ванн') || q.includes('санузел') || q.includes('плесен')) {
            return 'Санитарный силикон! Битва с плесенью.\n\n• Бюджет — LARGOMIX санитарный белый, 10.29 BYN\n• Оптимум — Soudal санитарный белый, 22.08 BYN\n• Премиум — Ceresit санитарный белый, 18.06 BYN\n\nСовет: сначала убрать старый, обработать антигрибковым, просушить сутки.';
        }
        if (q.includes('нейтральн')) {
            return 'Нейтральный силикон! Универсальный, без запаха.\n\n• Bostik нейтральный, 16.17 BYN\n• Soudal нейтральный, 17.86 BYN\n• Ceresit нейтральный, 15.29 BYN\n\nСовет: подходит для камня, металла, стекла.';
        }
        if (q.includes('аквариум') || q.includes('рыб')) {
            return 'Силикон для аквариума? Только 100% силикон без добавок.\n\n• Soudal нейтральный прозрачный, 16.82 BYN\n• Ceresit нейтральный прозрачный, 10.42 BYN\n\nВажно: санитарный с антибактериальными добавками НЕЛЬЗЯ. Убьёт рыбок.';
        }
        if (q.includes('стекл') || q.includes('зеркал')) {
            return 'Силикон для стекла? Прозрачный нейтральный.\n\n• Soudal нейтральный прозрачный, 16.82 BYN\n• Ceresit нейтральный прозрачный, 10.42 BYN\n• Bostik нейтральный прозрачный, 16.17 BYN\n\nСовет: только прозрачный.';
        }
        if (q.includes('окн') || q.includes('рам')) {
            return 'Силикон для окон? Лучше акрил или MS.\n\n• Под покраску — акрил Soudal, 8.44 BYN\n• Без покраски — силикон нейтральный Soudal, 17.86 BYN\n• Для дерева — акрил\n\nСовет: для пластиковых окон — силикон нейтральный.';
        }
        if (q.includes('кухн') || q.includes('столешниц')) {
            return 'Силикон для кухни? Санитарный.\n\n• LARGOMIX санитарный прозрачный, 17.99 BYN\n• Soudal санитарный белый, 22.08 BYN\n• Ceresit санитарный, 23.15 BYN\n\nСовет: для столешницы — прозрачный. Для мойки — белый.';
        }
        if (q.includes('фасад') || q.includes('улиц')) {
            return 'Силикон для фасада? Можно, но лучше полиуретан.\n\n• Силикон нейтральный Soudal, 17.86 BYN\n• Полиуретан — для фасада лучше\n• Акрил — под покраску\n\nСовет: для фасада — атмосферостойкий.';
        }
        if (q.includes('какой') && q.includes('лучше')) {
            return 'Какой силикон лучше?\n\n• До 12 BYN — LARGOMIX, Bostik, Ceresit\n• 15–20 BYN — Soudal, Tytan\n• 20–25 BYN — Soudal санитарный, Ceresit санитарный\n\nДля быта хватит LARGOMIX.';
        }
        if (q.includes('сколько') || q.includes('расход')) {
            return 'Сколько силикона нужно?\n\n• 1 тюбик 280 мл = ~10–12 м шва\n• Ванная = 1–2 тюбика\n• Кухня = 1–2 тюбика\n• Окно = 0.5–1 тюбик\n\nСовет: берите с запасом.';
        }
        return 'Силикон! Король герметиков.\n\nУточним:\n1. Где — ванная, кухня, окна, фасад?\n2. Плесень есть?\n3. Внутри или снаружи?\n\n• Санитарный — Soudal, 22.08 BYN\n• Нейтральный — Ceresit, 15.29 BYN';
    }

    // АКРИЛ
    if (q.includes('акрил')) {
        if (q.includes('окн') || q.includes('рам')) {
            return 'Акрил для окон? Идеально. Под покраску.\n\n• Soudal акрил белый, 8.44 BYN\n• Ceresit акрил белый, 9.47 BYN\n• LARGOMIX акрил белый, 10.63 BYN\n\nСовет: наносите, разгладьте, покрасьте через 24 часа.';
        }
        if (q.includes('стен') || q.includes('трещин')) {
            return 'Акрил для стен и трещин? Да.\n\n• Soudal акрил, 8.44 BYN\n• Ceresit акрил, 9.47 BYN\n• LARGOMIX акрил, 10.63 BYN\n\nСовет: трещину расширить, очистить, загрунтовать.';
        }
        if (q.includes('потолок')) {
            return 'Акрил для потолка? Под покраску — да.\n\n• Soudal акрил белый, 8.44 BYN\n• Ceresit акрил белый, 9.47 BYN\n\nСовет: берите белый.';
        }
        if (q.includes('силикон') && q.includes('разниц')) {
            return 'Акрил или силикон?\n\n• Акрил — под покраску, внутри, для стен и окон. Боится воды.\n• Силикон — влагостойкий, для ванной и кухни. Не красится.\n\nПравило:\n• Красить → акрил\n• Влажно → силикон\n• Улица → полиуретан или MS';
        }
        return 'Акрил! Герметик под покраску.\n\nУточним:\n1. Где — окна, стены, потолок?\n2. Будете красить?\n3. Внутри или снаружи?\n\n• Бюджет — Soudal акрил, 8.44 BYN\n• Оптимум — Ceresit акрил, 9.47 BYN\n• Премиум — LARGOMIX акрил, 10.63 BYN';
    }

    // ЭПОКСИД
    if (q.includes('эпоксид') || q.includes('затирк') || q.includes('фуг')) {
        if (q.includes('ванн') || q.includes('санузел')) {
            return 'Эпоксид для ванной? Лучшее решение.\n\n• Mapei 1 кг, 83.13 BYN\n• Mapei 2 кг, 155.04 BYN\n• Litokol 1 кг, 154.41 BYN\n\nСовет: для ванной хватит 1–2 кг.';
        }
        if (q.includes('кухн') || q.includes('фартук')) {
            return 'Эпоксид для кухни? Да, для фартука идеально.\n\n• Mapei 1 кг, 83.13 BYN\n• Litokol 1 кг, 154.41 BYN\n\nСовет: эпоксид не боится жира и пара.';
        }
        if (q.includes('бассейн')) {
            return 'Эпоксид для бассейна? Обязательно.\n\n• Mapei 2.5 кг, 255.79 BYN\n• Mapei 5 кг, 92.84 BYN\n• Litokol 2.5 кг, 152.29 BYN\n\nСовет: только эпоксид.';
        }
        if (q.includes('mapei') && q.includes('litokol')) {
            return 'Mapei или Litokol? Оба топ.\n\n• Mapei — дешевле, 83 BYN за 1 кг\n• Litokol — премиальнее, 154 BYN за 1 кг\n\nБерите что дешевле.';
        }
        return 'Эпоксидная затирка! Тяжёлая артиллерия.\n\nУточним:\n1. Где — ванная, кухня, бассейн?\n2. Шов какой — 2 мм, 5 мм?\n3. Цвет?\n\n• Mapei — от 83.13 BYN\n• Litokol — от 154.41 BYN';
    }

    // СИЗ
    if (q.includes('сиз') || q.includes('защит') || q.includes('респиратор') || q.includes('перчатк')) {
        if (q.includes('респиратор') && q.includes('покрас')) {
            return 'Респиратор для покраски? Нужен FFP2 или FFP3.\n\n• CCK FFP1, 4.72 BYN (для пыли)\n• Specovka FFP1, 16.02 BYN\n• Robinzon FFP1, 25.12 BYN\n\nСовет: для красок — с угольным фильтром.';
        }
        if (q.includes('респиратор') && q.includes('пыл')) {
            return 'Респиратор от пыли? FFP1 хватит.\n\n• CCK FFP1, 4.72 BYN\n• Stroimhatu FFP1, 6.33 BYN\n• Europrotect FFP1, 23.28 BYN\n\nСовет: для бетонной пыли — FFP2.';
        }
        if (q.includes('перчатк') && (q.includes('нитрил') || q.includes('хими'))) {
            return 'Нитриловые перчатки! Лучшее для химии.\n\n• Dilins одноразовые, 2.92 BYN\n• MY1230 одноразовые, 14.97 BYN\n• Europrotect многоразовые, 18.15 BYN\n\nСовет: для растворителей — только нитрил.';
        }
        if (q.includes('перчатк') && q.includes('стройк')) {
            return 'Перчатки для стройки?\n\n• Точные работы — Dilins, 2.92 BYN\n• Монтаж — Europrotect, 18.15 BYN\n• Тяжёлые — кожаные или спилковые\n\nСовет: нитрил не боится масла и химии.';
        }
        if (q.includes('комплект') || q.includes('полный')) {
            return 'Полный комплект СИЗ?\n\n• Респиратор FFP1 — от 4.72 BYN\n• Перчатки нитриловые — от 2.92 BYN\n• Очки — уточните наличие\n\nИтого: от 7.64 BYN за базовый.';
        }
        return 'СИЗ! Тут не до шуток. Безопасность прежде всего.\n\nУточним:\n1. Что нужно — респиратор, перчатки?\n2. Для какой работы — покраска, шлифовка, химия?\n3. Разово или постоянно?\n\n• Респираторы — от 4.72 BYN\n• Перчатки — от 2.92 BYN';
    }

    // УНИВЕРСАЛЬНЫЕ
    if (q.includes('не знаю') || q.includes('что нужно') || q.includes('помоги')) {
        return 'Обожаю этот момент. Как прийти в ресторан и сказать «ну, что-нибудь».\n\nЛадно. Допрос:\n1. Что происходит — сломалось, отвалилось, течёт, скрипит?\n2. Где — дом, улица, авто, гараж?\n3. Что хотите — «чтоб держалось», «чтоб не текло»?\n\nОтвечайте — и у меня будет план.';
    }
    if (q.includes('посовету') || q.includes('рекоменд') || q.includes('что купить')) {
        return 'Советую начать с задачи. Что делаете?\n\n• Клеите → MS-полимер или клей-пена\n• Герметизируете → силикон или акрил\n• Красите → акрил\n• Плитку → эпоксидная затирка\n• Защита → СИЗ\n\nОпишите задачу — подберу точно.';
    }
    if (q.includes('дёшев') || q.includes('дешев') || q.includes('бюджет') || q.includes('эконом')) {
        return 'Дёшево? Уважаю. Вот бюджетные варианты:\n\n• Силикон — LARGOMIX, 10.29 BYN\n• Акрил — Soudal, 8.44 BYN\n• Клей-пена — Soudal, 14.25 BYN\n• MS-полимер — Tytan Fix Seal, 32 BYN\n• Респиратор — CCK, 4.72 BYN\n• Перчатки — Dilins, 2.92 BYN\n\nСовет: на СИЗ не экономьте.';
    }
    if (q.includes('премиум') || q.includes('лучш') || q.includes('качеств') || q.includes('профи')) {
        return 'Премиум? Тогда вот:\n\n• MS-полимер — Sika, 58 BYN\n• Клей-пена — Penosil, 28.70 BYN\n• Силикон — Soudal санитарный, 22.08 BYN\n• Эпоксид — Litokol, 154.41 BYN\n• Респиратор — Robinzon, 25.12 BYN\n\nСовет: премиум = стабильность.';
    }
    if (q.includes('срочно') || q.includes('быстро') || q.includes('сегодня')) {
        return 'Срочно? Понял. Без шуток.\n\nЧто случилось? Течёт, отвалилось, сломалось?\n\n• Течёт — сначала перекройте воду. Потом герметик.\n• Отвалилось — крепёж + клей.\n• Сломалось — эпоксид.\n\nОпишите — подберу за 10 секунд.';
    }
    if (q.includes('улиц') || q.includes('наруж') || q.includes('фасад') || q.includes('снаруж')) {
        return 'Для улицы? Тут важна атмосферостойкость.\n\n• Герметик — силикон нейтральный или полиуретан\n• Клей — MS влагостойкий (Sika, Mapei)\n• Пена — влагостойкая (Penosil, WUNDER)\n• Затирка — эпоксидная\n\nСовет: не берите акрил и обычный силикон.';
    }
    if (q.includes('для дома') || q.includes('квартир') || q.includes('бытов')) {
        return 'Для дома? Всё проще.\n\n• Силикон — Soudal санитарный, 22.08 BYN\n• Акрил — Soudal, 8.44 BYN\n• Клей-пена — Soudal, 14.25 BYN\n• MS-полимер — Tytan, 35 BYN\n• СИЗ — CCK, 4.72 BYN\n\nСовет: хватит бюджетных. Профи не нужен.';
    }
    if (q.includes('производств') || q.includes('завод') || q.includes('цех')) {
        return 'Для производства? Нужны объёмы и стабильность.\n\n• MS-полимер — Sika, Mapei (опт)\n• Клей-пена — Penosil, WUNDER (опт)\n• Эпоксид — Litokol, Mapei (опт)\n• СИЗ — Robinzon, Europrotect (опт)\n\nСовет: для производства — B2B-условия.';
    }

    // БИБЛИОТЕКА
    if (q.includes('как нанос') || q.includes('как примен') || q.includes('инструкц')) {
        return 'Инструкция? Есть план.\n\n1. Очистить поверхность\n2. Обезжирить\n3. Просушить\n4. Нанести состав\n5. Разгладить\n6. Дать высохнуть 24 часа\n\n📖 Подробная инструкция — в «Библиотеке».';
    }
    if (q.includes('как выбрать') || q.includes('как подобрать')) {
        return 'Как выбрать? Три вопроса:\n\n1. Что делаете? (клеите, герметизируете, крепите)\n2. Где? (внутри, снаружи, влажно)\n3. Что важно? (дёшево, надёжно, быстро)\n\nОтвечайте — и у меня будет план.\n\n📖 Подробнее — в «Библиотеке».';
    }
    if (q.includes('ошибк') || q.includes('не держ') || q.includes('отвал')) {
        return 'Ошибки? Классика:\n\n• Не очистили → отвалилось\n• Не обезжирили → не держит\n• Нанесли на влажное → пузыри\n• Мало клея → отвалилось\n• Много клея → выдавило\n• Не дали высохнуть → сдвинулось\n\n📖 Подробнее — в «Библиотеке».';
    }
    if (q.includes('совет') || q.includes('лайфхак') || q.includes('хитрост')) {
        return 'Совет? Держите:\n\n• Герметик разглаживайте мыльной водой\n• Пену увлажняйте перед нанесением\n• Эпоксид смешивайте ровно 1:1\n• Силикон не красится — берите акрил\n• Для улицы — полиуретан, не силикон\n\n📖 Больше советов — в «Библиотеке».';
    }
    if (q.includes('документац') || q.includes('сертификат') || q.includes('паспорт')) {
        return 'Документация? Всё есть.\n\n• Сертификаты соответствия\n• Паспорта качества\n• Декларации\n\n📄 В разделе «Документы и сертификаты».';
    }

    // ПО МАТЕРИАЛУ
    if (q.includes('бетон')) {
        return 'Бетон! Тут главное — крепёж.\n\n• Дюбель универсальный + саморез\n• Анкер-клин для тяжёлого\n• Для герметизации — полиуретан\n\nСовет: для бетона — перфоратор.';
    }
    if (q.includes('кирпич')) {
        return 'Кирпич! Тут дюбель обычный не всегда держит.\n\n• Дюбель универсальный 8×40\n• Для пустотелого — специальный дюбель\n• Для тяжёлого — анкер\n\nСовет: в пустотелый — только химический анкер.';
    }
    if (q.includes('гипсокартон') || q.includes('гкл')) {
        return 'Гипсокартон! Не слабый, просто нежный.\n\n• До 10 кг — дюбель Driva\n• 10–20 кг — дюбель Molly\n• 20+ кг — крепление в профиль\n\nСовет: не вешайте на один дюбель.';
    }
    if (q.includes('дерев') || q.includes('доск') || q.includes('брус')) {
        return 'Дерево! Тут клей и крепёж.\n\n• Клей — ПВА или MS-полимер\n• Крепёж — саморез по дереву\n• Защита — лак или краска\n\nСовет: для улицы — влагостойкий клей.';
    }
    if (q.includes('металл')) {
        return 'Металл! Тут эпоксид и крепёж.\n\n• Клей — эпоксидный\n• Крепёж — саморез по металлу, заклёпка\n• Защита — грунт по металлу\n\nСовет: металл обезжирить.';
    }
    if (q.includes('пластик')) {
        return 'Пластик! Материал с характером.\n\n• ABS, ПВХ — MS или цианоакрилат\n• Полипропилен — праймер + спецклей\n• Полиэтилен — почти не клеится\n\nСовет: зашкурить перед склейкой.';
    }
    if (q.includes('стекл')) {
        return 'Стекло! Тут прозрачный клей.\n\n• Клей — цианоакрилат для стекла\n• Герметик — силикон нейтральный прозрачный\n• Крепёж — специальные держатели\n\nСовет: не используйте эпоксид — шов будет виден.';
    }
    if (q.includes('камен') || q.includes('мрамор') || q.includes('гранит')) {
        return 'Камень! Только нейтральные составы.\n\n• Клей — MS-полимер белый\n• Герметик — силикон нейтральный\n• Затирка — эпоксидная\n\nСовет: кислотный силикон повредит камень.';
    }
    if (q.includes('плитк') || q.includes('керамогранит')) {
        return 'Плитка! Тут затирка и клей.\n\n• Затирка — эпоксидная (Mapei, Litokol)\n• Клей — плиточный\n• Герметик — силикон санитарный\n\nСовет: для влажных зон — эпоксид.';
    }
    if (q.includes('пенопласт') || q.includes('ппс') || q.includes('утеплит')) {
        return 'Пенопласт! Тут клей-пена.\n\n• Клей-пена — Soudal, Ceresit\n• Клей — специальный для пенопласта\n• Крепёж — дюбель-грибок\n\nСовет: не используйте растворители. Растворят.';
    }

    // СРАВНЕНИЯ
    if (q.includes('soudal') && q.includes('ceresit')) {
        return 'Soudal или Ceresit? Оба топ.\n\n• Soudal — бельгийский, чуть дороже\n• Ceresit — немецкий, чуть дешевле\n\nРазница: Soudal чуть лучше. Ceresit — по цене.\n\nБерите что дешевле.';
    }
    if (q.includes('tytan') && q.includes('soudal')) {
        return 'Tytan или Soudal?\n\n• Tytan — польский, дешевле\n• Soudal — бельгийский, дороже\n\nРазница: Soudal стабильнее. Tytan — бюджетнее.\n\nДля дома — Tytan. Для профи — Soudal.';
    }
    if (q.includes('mapei') && q.includes('litokol')) {
        return 'Mapei или Litokol?\n\n• Mapei — дешевле\n• Litokol — премиальнее\n\nДля быта — Mapei. Для профи — Litokol.';
    }
    if (q.includes('российск') || q.includes('импортн') || q.includes('отечествен')) {
        return 'Российские или импортные?\n\n• Импортные (Soudal, Ceresit, Mapei) — стабильнее\n• Российские (LARGOMIX, Profpur, Belineco) — дешевле\n\nДля быта — российские. Для профи — импортные.';
    }
    if (q.includes('топ') || q.includes('популярн') || q.includes('хит')) {
        return 'Топ-5 товаров Mr. Fix:\n\n1. Soudal клей-пена 750 мл — 14.25 BYN\n2. Soudal силикон санитарный — 22.08 BYN\n3. Tytan Fix Seal MS — 32 BYN\n4. CCK респиратор FFP1 — 4.72 BYN\n5. Dilins перчатки — 2.92 BYN\n\nСовет: берите что нужно.';
    }

    // СПЕЦИАЛЬНЫЕ
    if (q.includes('ванн') || q.includes('плесен')) {
        return 'Ванная! Моё любимое место для заговоров против плесени.\n\nЕсть план:\n1. Шов где — стык ванны, стены, раковины?\n2. Плесень уже есть?\n3. Цвет — белый, прозрачный?\n\nЕсли плесень есть:\n1. Убрать старый герметик\n2. Обработать антигрибковым\n3. Просушить сутки\n4. Soudal санитарный белый, 22.08 BYN';
    }
    if (q.includes('полк')) {
        return 'Полка! Отличный повод что-нибудь сломать. Шучу. Или нет.\n\nУточним:\n1. Стена — бетон, кирпич, гипсокартон?\n2. Вес полки?\n\nЕсли гипсокартон:\n• Дюбель Driva или Molly\n• 2–3 точки крепления\n• Саморезы 4×40\n\nСовет: не вешайте на один дюбель.';
    }
    if (q.includes('скрип') || q.includes('дверц') || q.includes('петл')) {
        return 'Скрип. Классика. Шкаф жалуется.\n\nПлан:\n• Смазка Silicone Spray для петель\n• Если петля разболталась — дюбель + саморез\n• Если дверца провисла — отрегулировать\n\nНе надо: подсолнечное масло.';
    }
    if (q.includes('срочно') || q.includes('течёт') || q.includes('течет')) {
        return 'Понял, без шуток. Течь — серьёзно.\n\nЕсли труба под давлением — перекройте воду, вызовите сантехника.\nЕсли нужно временно — Mr. Fix Silicone или лента для труб.\n\nВажно: это не постоянное решение.';
    }
    if (q.includes('газ')) {
        return 'Стоп. Газ — это не шутки и не герметик.\n\nНельзя: герметизировать газовую трубу самостоятельно.\nНужно: вызвать газовую службу. Немедленно.\n\nЕсли чувствуете запах газа: откройте окна, не включайте свет, выйдите на улицу, позвоните 104.';
    }
    if (q.includes('кот') || q.includes('кота')) {
        return 'Так. Кота — не надо. Кот — это не задача, это живое существо. И оно против.\n\nЕсли серьёзно: ничем. Кот отвалится. И будет мстить.';
    }
    if (q.includes('крепёж') || q.includes('крепеж') || q.includes('дюбел') || q.includes('саморез')) {
        return 'Крепёж! Главное — основание и вес.\n\nУточним:\n1. Стена — бетон, кирпич, гипсокартон?\n2. Что вешаем и сколько весит?\n3. Внутри или снаружи?\n\nОтвечайте — и будет точный план.';
    }
    if (q.includes('герметик') || q.includes('герметиз')) {
        return 'Герметик! Три плана: силикон, акрил, полиуретан.\n\nУточним:\n1. Где — санузел, окна, фасад, авто?\n2. Что важно — от воды, от плесени, под покраску?\n3. Внутри или снаружи?\n\nОтвечайте — и подберу точно.';
    }
    if (q.includes('клей') || q.includes('скле')) {
        return 'Клей! Главное — что склеиваем и нагрузка.\n\nУточним:\n1. Что склеиваем — дерево, металл, пластик, стекло?\n2. Нагрузка будет?\n3. Внутри или на улице?\n\n• Дерево — ПВА или MS\n• Металл — эпоксид\n• Пластик — MS или цианоакрилат\n• Стекло — цианоакрилат';
    }

    return '🤔 Я вас понял, но нужно уточнить. Расскажите:\n\n1. Что нужно — герметик, клей или крепёж?\n2. Что делаете — какая задача?\n3. Где — дом, улица, авто, производство?\n\nИ у меня будет план. Целых три.';
}

// ============================================================
// ГОЛОС
// ============================================================
function toggleVoice() {
    if (!recognition) initVoiceRecognition();
    if (isVoiceListening) {
        recognition.stop();
        isVoiceListening = false;
        aiVoiceBtn.classList.remove('active');
        aiVoiceBtn.innerHTML = '<i class="fas fa-microphone"></i>';
    } else {
        try { recognition.start(); } catch (e) { initVoiceRecognition(); recognition.start(); }
    }
}

function initVoiceRecognition() {
    const SR = window.SpeechRecognition || window.webkitSpeechRecognition;
    if (!SR) {
        showNotification('❌ Голосовой ввод не поддерживается');
        return;
    }
    recognition = new SR();
    recognition.lang = 'ru-RU';
    recognition.continuous = false;
    recognition.interimResults = true;
    recognition.onstart = () => {
        isVoiceListening = true;
        aiVoiceBtn.classList.add('active');
        aiVoiceBtn.innerHTML = '<i class="fas fa-stop"></i>';
    };
    recognition.onresult = (event) => {
        let final = '';
        for (let i = event.resultIndex; i < event.results.length; i++) {
            if (event.results[i].isFinal) final += event.results[i][0].transcript;
        }
        if (final) {
            aiInput.value = final;
            setTimeout(() => aiSend(), 300);
        }
    };
    recognition.onend = () => {
        isVoiceListening = false;
        aiVoiceBtn.classList.remove('active');
        aiVoiceBtn.innerHTML = '<i class="fas fa-microphone"></i>';
    };
}

function showNotification(text) {
    const existing = document.querySelector('.notification');
    if (existing) existing.remove();
    const div = document.createElement('div');
    div.className = 'notification';
    div.textContent = text;
    document.body.appendChild(div);
    setTimeout(() => {
        div.style.opacity = '0';
        setTimeout(() => div.remove(), 500);
    }, 3000);
}

window.addEventListener('scroll', () => {
    const header = document.getElementById('header');
    if (window.scrollY > 20) header.classList.add('scrolled');
    else header.classList.remove('scrolled');
});

function handleReveal() {
    const reveals = document.querySelectorAll('.reveal');
    const windowHeight = window.innerHeight;
    reveals.forEach(el => {
        const rect = el.getBoundingClientRect();
        if (rect.top < windowHeight - 80) el.classList.add('visible');
    });
}

document.addEventListener('DOMContentLoaded', () => {
    renderCatalog();
    populateFilters();
    renderPriceAccordion(productsData);
    renderLibrary();
    renderReviews();
    updateCartCount();
    setTimeout(handleReveal, 300);
    window.addEventListener('scroll', handleReveal);
});
</script>
</body>
</html>
