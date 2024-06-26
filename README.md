# SQL-data-cleaning
This is an educational project on data cleaning and preparation using SQL. The original database in CSV format is located in the file club_member_info.csv. Here, we will explore the steps that need to be applied to obtain a cleansed version of the dataset.
## Mô tả dữ liệu
|full_name|age|martial_status|email|phone|full_address|job_title|membership_date|
|---------|---|--------------|-----|-----|------------|---------|---------------|
|addie lush|40|married|alush0@shutterfly.com|254-389-8708|3226 Eastlawn Pass,Temple,Texas|Assistant Professor|7/31/2013|
|      ROCK CRADICK|46|married|rcradick1@newsvine.com|910-566-2007|4 Harbort Avenue,Fayetteville,North Carolina|Programmer III|5/27/2018|
|Sydel Sharvell|46|divorced|ssharvell2@amazon.co.jp|702-187-8715|4 School Place,Las Vegas,Nevada|Budget/Accounting Analyst I|10/6/2017|
|Constantin de la cruz|35||co3@bloglines.com|402-688-7162|6 Monument Crossing,Omaha,Nebraska|Desktop Support Technician|10/20/2015|
|  Gaylor Redhole|38|married|gredhole4@japanpost.jp|917-394-6001|88 Cherokee Pass,New York City,New York|Legal Assistant|5/29/2019|

## Tạo bảng mới

```sql
CREATE TABLE club_member_info_clean (
	full_name VARCHAR(50),
	age INTEGER,
	martial_status VARCHAR(50),
	email VARCHAR(50),
	phone VARCHAR(50),
	full_address VARCHAR(50),
	job_title VARCHAR(50),
	membership_date VARCHAR(50)
);
```

## Lấy dữ liệu từ bảng gốc

```sql
INSERT INTO club_member_info_clean
select * from club_member_info
```

## Chuyển đổi dữ liệu cột full_name thành chữ in hoa
```sql
UPDATE club_member_info_clean SET full_name = UPPER(full_name)
```

## Loại bỏ khoảng trống trong dữ liệu cột full_name 
```sql
UPDATE club_member_info_clean SET full_name = TRIM(full_name)
```

## Chuyển đổi các giá trị trống và giá trị phi thực tế trong cột age thành 45 (trung bình)
```sql
UPDATE club_member_info_clean SET age = 45 WHERE  age > 68 OR age ISNULL
```

## Chỉnh sửa giá trị lỗi trong cột martial_status
```sql
UPDATE club_member_info_clean SET martial_status = 'divorced' WHERE martial_status = 'divored'
```

## Chuyển đổi các giá trị trống trong cột martial_staus thành married (trung vị)
```sql
UPDATE club_member_info_clean SET martial_status = 'married'  WHERE martial_status = ''
```

## Chuyển đổi các giá trị trống trong cột phone thành Unknown
```sql
UPDATE club_member_info_clean SET martial_status = 'married'  WHERE martial_status = ''
```

## Chuyển đổi các giá trị trống trong cột job_title thành Unknown
```sql
UPDATE club_member_info_clean SET job_title = 'Unknown' WHERE job_title  = ''
```
