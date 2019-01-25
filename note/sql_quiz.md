11.通过 SQL，您如何在表 Persons 中选择 FirstName 等于 Thomas 而 LastName 等于 Carter 的所有记录？
您的回答：SELECT * FROM Persons WHERE FirstName LIKE 'Thomas' AND LastName LIKE 'Carter'

正确答案：SELECT * FROM Persons WHERE FirstName='Thomas' AND LastName='Carter'

12.通过 SQL，您如何按字母顺序选取 Persons 表中 LastName 介于 Adams 和 Carter 的所有记录？
您的回答：SELECT * FROM Persons WHERE LastName>'Adams' AND LastName<'Carter'

正确答案：SELECT * FROM Persons WHERE LastName BETWEEN 'Adams' AND 'Carter'