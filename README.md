# Pizza-sales-analysis

Cleaned a pizza sales dataset of over 21,000 orders and ran SQL queries to extract key metrics, such as monthly sales
growth and top 5 best-selling pizzas.

Created an interactive dashboard to visualize sales performance, identify product demand, and enable data-driven
decision-making.

SQL Commands-

select * from pizza_sales;

Total revenue:

select sum(total_price) as total_revenue from pizza_sales;

Avg order value:

select sum(total_price)/count(distinct(order_id)) as avg_order_value from pizza_sales;

Total pizza sold:

select sum(quantity) as total_pizza_sold from pizza_sales;

Total orderS placed:

select count(distinct(order_id)) as total_orders from pizza_sales;

Avg pizzas per order:

select sum(quantity)/count(distinct(order_id)) as avg_pizzas_per_order from pizza_sales;

Orders by day:

select dayname(order_date) as day_name,count(distinct(order_id)) as total_pizzas from pizza_sales
group by day_name;

Orders by month:

select monthname(order_date) as month_name,count(distinct(order_id)) as total_pizzas from pizza_sales
group by month_name;

Percentage of sales by pizza category:

select pizza_category,(sum(quantity)/(select sum(quantity) from pizza_sales))*100 as perc from pizza_sales
group by pizza_category;

Percentage of sales by pizza size:

select pizza_size,(sum(quantity)/(select sum(quantity) from pizza_sales))*100 as perc from pizza_sales
group by pizza_size;

Top 5 Pizzas by Revenue:

select pizza_name_id,sum(total_price) as total_revenue from pizza_sales
group by pizza_name_id order by total_revenue desc limit 5;

Bottom 5 Pizzas by Revenue:

select pizza_name_id,sum(total_price) as total_revenue from pizza_sales
group by pizza_name_id order by total_revenue asc limit 5;

Top 5 Pizzas by Quantity:

select pizza_name_id,sum(quantity) as total_amt from pizza_sales
group by pizza_name_id order by total_amt desc limit 5;

Bottom 5 Pizzas by Quantity:

select pizza_name_id,sum(quantity) as total_amt from pizza_sales
group by pizza_name_id order by total_amt asc limit 5;

Top 5 Pizzas by Total Orders:

select pizza_name_id,count(distinct(order_id)) as total_no from pizza_sales
group by pizza_name_id order by total_no desc limit 5;

Bottom 5 Pizzas by Total Orders:

select pizza_name_id,count(distinct(order_id)) as total_no from pizza_sales
group by pizza_name_id order by total_no asc limit 5;
