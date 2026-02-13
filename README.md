# Windows_fun


use analyticfun;

select * from aggregatefun;

select name,department,salary,
	min(salary) over(partition by department order by salary) as result 
    from aggregatefun;

select * from aggregatefun;

select *, row_number() over(order by department) as `dack` from aggregatefun;


select * from percent_cume;

select *, cume_dist() over(order by sales) as `result` from percent_cume;


select * from value_function;

select name,department,salary, lag(salary) over(order by salary) as `previous_value` 
	from value_function;
    

select name,department,salary, lead(salary) over(order by salary) as `Next_value` 
	from value_function limit 3;

select name,department,salary, first_value(salary) over(order by salary) as `Next_value` 
	from value_function;
    
select name,department,salary, last_value(salary) over(order by salary) as `Next_value` 
	from value_function;
    
SELECT *, LAST_VALUE(salary) OVER(ORDER BY salary
	ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) 
		AS Highest_Salary FROM value_function;


select name,department,salary, nth_value(salary,2) over(order by salary) as `Second_Lowest_Sal` 
	from value_function;
    
SELECT salary
FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS `DR`
    FROM value_function
) AS second_highest
WHERE DR = 2;

    






    


    

