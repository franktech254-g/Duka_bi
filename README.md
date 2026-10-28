import flet as ft
from datetime import datetime

def main(page: ft.Page):
    page.bgcolor = "#7A1A2A"  # BEHARV MAROON
    page.padding = 0
    page.scroll = "auto"
    page.title = "DUKA BI Pro"

    # --- DATA (from your screenshot) ---
    sales_today = "KSh 420.00"
    expenses_today = "KSh 200.00"
    products = "3"
    stock_value = "KSh 5,500.00"

    # --- HERO SECTION (Like BEHARV screenshot) ---
    def hero_section():
        return ft.Container(
            bgcolor="#7A1A2A",
            padding=20,
            content=ft.Column([
                # Top bar
                ft.Row([
                    ft.Icon(ft.Icons.MENU, color="white"),
                    ft.Row([ft.Icon(ft.Icons.SCHOOL, color="white"), ft.Text("BEHARV", color="white", weight="bold", size=18)], alignment="center"),
                    ft.Icon(ft.Icons.SEARCH, color="white")
                ], alignment="spaceBetween"),
                ft.Container(height=20),
                # Image
                ft.Container(
                    border_radius=20,
                    clip_behavior=ft.ClipBehavior.ANTI_ALIAS,
                    content=ft.Image(
                        src="https://images.unsplash.com/photo-1553729459-efe14ef6055d?w=800",
                        height=220,
                        fit=ft.ImageFit.COVER,
                        width=float("inf")
                    )
                ),
                ft.Container(height=15),
                ft.Row([ft.Text("👆  Most accessed", color="#FFFFFFCC", size=12, letter_spacing=2),],),
                ft.Text("Financial and Accounting Management", color="white", size=26, weight="bold"),
                ft.Container(height=10),
                ft.Row([
                    ft.Container(bgcolor="#FFFFFF20", padding=ft.padding.symmetric(8,12), border_radius=20,
                                 content=ft.Row([ft.Icon(ft.Icons.MENU_BOOK, color="white", size=16), ft.Text("Administration and Management", color="white", size=11)])),
                    ft.Container(bgcolor="#FFFFFF20", padding=ft.padding.symmetric(8,12), border_radius=20,
                                 content=ft.Row([ft.Icon(ft.Icons.PEOPLE, color="white", size=16), ft.Text("20,332 enrollments", color="white", size=11)])),
                ], wrap=True),
                ft.Container(
                    bgcolor="#FFFFFF20", padding=ft.padding.symmetric(8,12), border_radius=20,
                    content=ft.Row([ft.Icon(ft.Icons.ACCESS_TIME, color="white", size=16), ft.Text("22h of learning", color="white", size=11)])
                ),
                ft.Container(height=15),
                ft.Container(
                    bgcolor="white", border_radius=10, padding=15, alignment=ft.alignment.center,
                    content=ft.Row([ft.Icon(ft.Icons.PLAY_ARROW, color="#7A1A2A"), ft.Text("Free enrollment", color="#7A1A2A", weight="bold")], alignment="center")
                ),
                ft.Text("Optional certificate", color="#FFFFFF99", size=11),
            ])
        )

    # --- PROFESSIONAL DASHBOARD CARDS (Your DUKA BI) ---
    def dashboard_section():
        def p_card(label, value, color):
            return ft.Container(
                bgcolor="white", border_radius=16, padding=18, expand=1,
                shadow=ft.BoxShadow(blur_radius=10, color="#00000010"),
                content=ft.Column([
                    ft.Text(label, size=11, color="#64748B"),
                    ft.Container(height=8),
                    ft.Text(value, size=16, weight="bold", color=color)
                ])
            )

        return ft.Container(
            bgcolor="#F1F5F9",
            padding=20,
            border_radius=ft.border_radius.only(top_left=24, top_right=24),
            content=ft.Column([
                ft.Text("DASHBOARD • 2026-10-27", size=10, color="#64748B", letter_spacing=1),
                ft.Container(height=10),
                ft.Row([p_card("Sales today", sales_today, "#16A34A"), p_card("Expenses today", expenses_today, "#EA580C")], spacing=12),
                ft.Row([p_card("Products", products, "#2563EB"), p_card("Stock value (cost)", stock_value, "#0D9488")], spacing=12),
                ft.Container(height=20),
                ft.Text("QUICK ACTIONS", size=11, weight="bold", color="#334155"),
                ft.Text("Use the buttons below to manage products, sales, stock and expenses.", size=12, color="#64748B"),
                ft.Container(height=10),
                # Action buttons grid - professional
                ft.GridView(expand=False, runs_count=2, max_extent=180, spacing=10, run_spacing=10, height=320,
                    controls=[
                        ft.Container(bgcolor="white", border_radius=12, padding=15, on_click=lambda e: page.snack_bar.open(True),
                                     content=ft.Row([ft.Icon(ft.Icons.ADD_BOX, color="#334155"), ft.Text("Add product", size=12, weight="bold")])),
                        ft.Container(bgcolor="white", border_radius=12, padding=15,
                                     content=ft.Row([ft.Icon(ft.Icons.POINT_OF_SALE, color="#334155"), ft.Text("Record sale", size=12, weight="bold")])),
                        ft.Container(bgcolor="white", border_radius=12, padding=15,
                                     content=ft.Row([ft.Icon(ft.Icons.LOCAL_SHIPPING, color="#334155"), ft.Text("Receive stock", size=12, weight="bold")])),
                        ft.Container(bgcolor="white", border_radius=12, padding=15,
                                     content=ft.Row([ft.Icon(ft.Icons.REMOVE, color="#334155"), ft.Text("Record expense", size=12, weight="bold")])),
                        ft.Container(bgcolor="white", border_radius=12, padding=15,
                                     content=ft.Row([ft.Icon(ft.Icons.ASSESSMENT, color="#334155"), ft.Text("Stock report", size=12, weight="bold")])),
                        ft.Container(bgcolor="white", border_radius=12, padding=15,
                                     content=ft.Row([ft.Icon(ft.Icons.CALENDAR_TODAY, color="#334155"), ft.Text("Daily sales", size=12, weight="bold")])),
                    ]
                ),
                ft.Container(height=10),
                ft.Text("RECENT SALES", size=11, weight="bold", color="#334155"),
                ft.Container(bgcolor="white", border_radius=12, padding=15,
                             content=ft.Column([
                                 ft.Text("maize flour × 3 • KSh 420.00", size=13),
                                 ft.Text("CASH", size=11, weight="bold", color="#64748B")
                             ]))
            ])
        )

    page.add(
        hero_section(),
        dashboard_section()
    )
    page.snack_bar = ft.SnackBar(ft.Text("Feature coming in v5.1!"))

ft.app(target=main)
