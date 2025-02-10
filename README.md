sql code for SSMS 2012 -> SELECT '[' + STUFF((
    SELECT ',{"ITEM_ID":' + CAST(ITEM_ID AS VARCHAR(10)) +
           ',"ItemName":"' + ItemName + '"' +
           ',"Barcode":"' + Barcode + '"' +
           ',"Cost":' + CAST(Cost AS VARCHAR(10)) +
           ',"Price":' + CAST(Price AS VARCHAR(10)) +
           ',"SinhalaName":"' + SinhalaName + '"' +
           ',"BillPrice":' + CAST(BillPrice AS VARCHAR(10)) +
           ',"Wholesale":' + CAST(Wholesale AS VARCHAR(10)) + '}'
    FROM [dbAxia].[dbo].[iteminformation]
    FOR XML PATH(''), TYPE).value('.', 'NVARCHAR(MAX)'), 1, 1, '') + ']'
AS JSON_Output

# Run sql code and save file as items.txt
# Then open txt file and remove Heading JSON_output
# Then insert date time row to array like below
{"ITEM_ID":1,"ItemName":"2022/10/21","Barcode":"22:30","Cost":0,"Price":0,"SinhalaName":"DateTime","BillPrice":0,"Wholesale":0}
