---
title: 投影作業 (C#)
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: a044982c21246fd4e8c1cbdbb9801ae7b29d05c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="projection-operations-c"></a>投影作業 (C#)
投影是指將物件轉換成新形式的作業，而這個形式通常僅包含後續即將使用的屬性。 透過使用投影，您可以建構根據每個物件所建立的新型別。 您可以投影屬性並對其執行數學函式。 您也可以投影原始物件，而不進行任何變更。  
  
 執行投影的標準查詢運算子方法詳列於下一節。  
  
## <a name="methods"></a>方法  
  
|方法名稱|描述|C# 查詢運算式語法|更多資訊|  
|-----------------|-----------------|---------------------------------|----------------------|  
|選取|投影以轉換函式為基礎的值。|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|SelectMany|投影一連串以轉換函式為基礎的值，然後將這些值壓平合併成一個序列。|使用多個 `from` 子句|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>查詢運算式語法範例  
  
### <a name="select"></a>選用版  
 下列範例使用 `select` 子句，來投影字串清單中每個字串的第一個字母。  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a>SelectMany  
 下列範例使用多個 `from` 子句，來投影字串清單中每個字串的每個字。  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a>Select 與 SelectMany 的比較  
 `Select()` 和 `SelectMany()` 的工作是從來源值產生一或多個結果值。 `Select()` 會針對每個來源值產生一個結果值。 因此，整體結果是集合與來源集合中的項目數相同。 相反地，`SelectMany()` 會產生單一整體結果，其中包含串連自每個來源值的子集合。 當做引數傳遞至 `SelectMany()` 的轉換函式必須傳回每個來源值的可列舉值序列。 `SelectMany()` 會接著串連這些可列舉的序列，以建立一個大型的序列。  
  
 下列兩個圖顯示這兩個方法的動作之間的概念差異。 在每個案例中，假設選取器 (轉換) 函式會從每個來源值選取花朵陣列。  
  
 下圖描述 `Select()` 如何傳回其中的項目數與來源集合相同的集合。  
  
 ![Select&#40;&#41; 之動作的概念圖例](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 下圖描述 `SelectMany()` 如何將中繼陣列序列串連成一個最終結果值，其中包含每個中繼陣列中的所有值。  
  
 ![顯示 SelectMany&#40;&#41; 之動作的圖形。](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")  
  
### <a name="code-example"></a>程式碼範例  
 下列範例會比較 `Select()` 和 `SelectMany()` 的行為。 程式碼會從來源集合的每個花名清單中擷取前兩個項目，以建立「花束」(Bouquet)。 在此範例中，轉換函式 <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> 所使用的「單一值」本身就是值集合。 這需要額外的 `foreach` 迴圈，以列舉每個子序列中的每個字串。  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********              
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Linq>  
 [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [select 子句](../../../../csharp/language-reference/keywords/select-clause.md)  
 [如何：從多個來源填入物件集合 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [如何：使用群組將檔案分割成許多檔案 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
