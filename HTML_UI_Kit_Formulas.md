# Power Apps HTML UI Kit Formulas

This guide contains polished, professional HTML and CSS formulas that you can directly paste into a **HTML Text** control in Power Apps.

### Important Tips for Power Apps:
1. Ensure the HTML text control's **Padding** is set to `0` so the custom borders and shadows display correctly.
2. The formulas below use `&` to concatenate dynamic Power Apps data (like `ThisItem.Title`).
3. Single quotes (`'`) are used for HTML attributes (e.g., `class='my-class'`) to avoid needing to manually escape double quotes `""` in Power Apps.
4. Set the **HtmlText** property of the control to these formulas.

---

## 1. The Modern Profile / Detail Card
*Best for displaying deep details in a gallery or a standalone form.*

```powerapps
"
<style>
    .pa-card {
        background: #ffffff;
        border-radius: 12px;
        box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        padding: 24px;
        font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
        border: 1px solid #e5e7eb;
        box-sizing: border-box;
        height: 100%;
    }
    .pa-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 16px;
    }
    .pa-title {
        font-size: 1.25rem;
        font-weight: 600;
        color: #111827;
        margin: 0;
    }
    .pa-subtitle {
        font-size: 0.875rem;
        color: #6b7280;
        margin-top: 4px;
    }
    .pa-divider {
        height: 1px;
        background-color: #f3f4f6;
        border: none;
        margin: 16px 0;
    }
    .pa-body {
        font-size: 0.95rem;
        color: #4b5563;
        line-height: 1.5;
    }
</style>
<div class='pa-card'>
    <div class='pa-header'>
        <div>
            <h2 class='pa-title'>" & ThisItem.Title & "</h2>
            <div class='pa-subtitle'>" & ThisItem.Category & "</div>
        </div>
    </div>
    <div class='pa-body'>
        " & ThisItem.Description & "
    </div>
    <hr class='pa-divider' />
    <div class='pa-subtitle'>Updated: " & Text(ThisItem.Modified, DateTimeFormat.ShortDate) & "</div>
</div>
"
```

---

## 2. The Interactive List Row (with Status Badge)
*Best for high-density Gallery views. Creates a clean, clickable-looking list.*

```powerapps
"
<style>
    .pa-row {
        display: flex;
        align-items: center;
        padding: 12px 16px;
        background: #ffffff;
        border-bottom: 1px solid #f3f4f6;
        font-family: 'Segoe UI', sans-serif;
        box-sizing: border-box;
    }
    .pa-avatar {
        width: 48px;
        height: 48px;
        border-radius: 50%;
        background: linear-gradient(135deg, #6366f1 0%, #4f46e5 100%);
        color: white;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.25rem;
        font-weight: 600;
        margin-right: 16px;
    }
    .pa-info {
        flex: 1;
    }
    .pa-name {
        margin: 0 0 4px 0;
        font-size: 1rem;
        font-weight: 600;
        color: #111827;
    }
    .pa-email {
        margin: 0;
        font-size: 0.875rem;
        color: #6b7280;
    }
    .pa-badge {
        padding: 4px 12px;
        border-radius: 9999px;
        font-size: 0.75rem;
        font-weight: 600;
        text-transform: uppercase;
        letter-spacing: 0.05em;
    }
    .badge-success { background: #d1fae5; color: #065f46; }
    .badge-warning { background: #fef3c7; color: #92400e; }
    .badge-error { background: #fee2e2; color: #991b1b; }
</style>
<div class='pa-row'>
    <div class='pa-avatar'>" & Left(ThisItem.FullName, 1) & "</div>
    <div class='pa-info'>
        <h4 class='pa-name'>" & ThisItem.FullName & "</h4>
        <p class='pa-email'>" & ThisItem.Email & "</p>
    </div>
    <div class='pa-badge " & 
        Switch(ThisItem.Status,
            ""Active"", ""badge-success"",
            ""Pending"", ""badge-warning"",
            ""badge-error""
        ) & "'>
        " & ThisItem.Status & "
    </div>
</div>
"
```

---

## 3. The Modern KPI / Dashboard Metric Card
*Best for Dashboards. Displays a large metric value with a positive/negative trend indicator.*

```powerapps
"
<style>
    .kpi-container {
        font-family: 'Segoe UI', sans-serif;
        background: #ffffff;
        border-radius: 16px;
        padding: 24px;
        border: 1px solid #e5e7eb;
        box-shadow: 0 1px 3px rgba(0,0,0,0.05);
        display: flex;
        flex-direction: column;
        position: relative;
        overflow: hidden;
        box-sizing: border-box;
        height: 100%;
    }
    .kpi-container::before {
        content: '';
        position: absolute;
        top: 0; left: 0; width: 100%; height: 4px;
        background: linear-gradient(90deg, #3b82f6, #2dd4bf);
    }
    .kpi-title {
        color: #6b7280;
        font-size: 0.875rem;
        font-weight: 600;
        text-transform: uppercase;
        letter-spacing: 0.05em;
        margin: 0;
    }
    .kpi-value {
        color: #111827;
        font-size: 2.25rem;
        font-weight: 700;
        margin: 12px 0;
        line-height: 1;
    }
    .kpi-trend {
        display: flex;
        align-items: center;
        font-size: 0.875rem;
        font-weight: 600;
    }
    .trend-positive { color: #10b981; }
    .trend-negative { color: #ef4444; }
    .trend-neutral { color: #6b7280; }
</style>
<div class='kpi-container'>
    <h3 class='kpi-title'>Total Revenue</h3>
    <div class='kpi-value'>" & Text(varRevenue, ""$#,##0"") & "</div>
    <div class='kpi-trend " & 
        If(varGrowth > 0, ""trend-positive"", varGrowth < 0, ""trend-negative"", ""trend-neutral"") & "'>
        " & If(varGrowth > 0, ""↑ "", varGrowth < 0, ""↓ "", ""- "") & 
        Text(Abs(varGrowth), ""0%"") & " vs last month
    </div>
</div>
"
```

---

## 4. Modern Progress Tracker
*Best for tracking percentage completion within a Gallery item or Form.*

```powerapps
"
<style>
    .progress-wrapper {
        font-family: 'Segoe UI', sans-serif;
        width: 100%;
        box-sizing: border-box;
    }
    .progress-header {
        display: flex;
        justify-content: space-between;
        margin-bottom: 8px;
        font-size: 0.875rem;
        font-weight: 600;
        color: #374151;
    }
    .progress-track {
        height: 8px;
        background-color: #e5e7eb;
        border-radius: 9999px;
        overflow: hidden;
    }
    .progress-fill {
        height: 100%;
        background: linear-gradient(90deg, #3b82f6, #8b5cf6);
        border-radius: 9999px;
    }
</style>
<div class='progress-wrapper'>
    <div class='progress-header'>
        <span>" & ThisItem.TaskName & "</span>
        <span>" & Text(ThisItem.CompletionPercentage, ""0%"") & "</span>
    </div>
    <div class='progress-track'>
        <div class='progress-fill' style='width: " & (ThisItem.CompletionPercentage * 100) & "%;'></div>
    </div>
</div>
"
```
