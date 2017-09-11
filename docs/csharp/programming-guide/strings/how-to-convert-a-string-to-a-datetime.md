---
title: "如何：將字串轉換為 DateTime (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting to DateTIme
ms.assetid: 88abef11-3a06-4b49-8dd2-61ed0e876fc3
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 15ef1ec4debf242cdabc42f26add890bd4b61507
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-a-string-to-a-datetime-c-programming-guide"></a><span data-ttu-id="b5993-102">如何：將字串轉換為 DateTime (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b5993-102">How to: Convert a String to a DateTime (C# Programming Guide)</span></span>
<span data-ttu-id="b5993-103">程式常讓使用者將日期輸入為字串值。</span><span class="sxs-lookup"><span data-stu-id="b5993-103">It is common for programs to enable users to enter dates as string values.</span></span> <span data-ttu-id="b5993-104">若要將字串型的日期轉換成 <xref:System.DateTime?displayProperty=fullName> 物件，您可以使用 <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> 方法或 <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> 靜態方法，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="b5993-104">To convert a string-based date to a <xref:System.DateTime?displayProperty=fullName> object, you can use the <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName> method or the <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> static method, as shown in the following example.</span></span>  
  
 <span data-ttu-id="b5993-105">**文化特性**。</span><span class="sxs-lookup"><span data-stu-id="b5993-105">**Culture**.</span></span>  <span data-ttu-id="b5993-106">世界各地的不同文化，有不同的日期字串撰寫方式。</span><span class="sxs-lookup"><span data-stu-id="b5993-106">Different cultures in the world write date strings in different ways.</span></span>  <span data-ttu-id="b5993-107">例如，01/20/2008 在美國是 January 20th, 2008。</span><span class="sxs-lookup"><span data-stu-id="b5993-107">For example, in the US 01/20/2008 is January 20th, 2008.</span></span>  <span data-ttu-id="b5993-108">在法國，這會擲回 InvalidFormatException。</span><span class="sxs-lookup"><span data-stu-id="b5993-108">In France this will throw an InvalidFormatException.</span></span> <span data-ttu-id="b5993-109">這是因為法國讀取的日期時間為日/月/年，而在美國是月/日/年。</span><span class="sxs-lookup"><span data-stu-id="b5993-109">This is because France reads date-times as Day/Month/Year, and in the US it is Month/Day/Year.</span></span>  
  
 <span data-ttu-id="b5993-110">因此，像 20/01/2008 這樣的字串在法國會剖析成 1 月 20 日 2008 年 ，但在美國會擲回 InvalidFormatException。</span><span class="sxs-lookup"><span data-stu-id="b5993-110">Consequently, a string like 20/01/2008 will parse to January 20th, 2008 in France, and then throw an InvalidFormatException in the US.</span></span>  
  
 <span data-ttu-id="b5993-111">若要判斷目前的文化特性設定，您可以使用 System.Globalization.CultureInfo.CurrentCulture。</span><span class="sxs-lookup"><span data-stu-id="b5993-111">To determine your current culture settings, you can use System.Globalization.CultureInfo.CurrentCulture.</span></span>  
  
 <span data-ttu-id="b5993-112">如需將字串轉換成 dateTime 的簡單範例，請參閱下例。</span><span class="sxs-lookup"><span data-stu-id="b5993-112">See the example below for a simple example of converting a string to dateTime.</span></span>  
  
 <span data-ttu-id="b5993-113">如需更多的日期字串範例，請參閱 <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="b5993-113">For more examples of date strings, see <xref:System.Convert.ToDateTime%28System.String%29?displayProperty=fullName>.</span></span>  
  
```csharp  
string dateTime = "01/08/2008 14:50:50.42";  
            DateTime dt = Convert.ToDateTime(dateTime);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt.Year, dt.Month, dt.Day, dt.Hour, dt.Minute, dt.Second, dt.Millisecond);  
            // Specify exactly how to interpret the string.  
            IFormatProvider culture = new System.Globalization.CultureInfo("fr-FR", true);  
  
            // Alternate choice: If the string has been input by an end user, you might    
            // want to format it according to the current culture:   
            // IFormatProvider culture = System.Threading.Thread.CurrentThread.CurrentCulture;  
            DateTime dt2 = DateTime.Parse(dateTime, culture, System.Globalization.DateTimeStyles.AssumeLocal);  
            Console.WriteLine("Year: {0}, Month: {1}, Day: {2}, Hour: {3}, Minute: {4}, Second: {5}, Millisecond: {6}",  
                              dt2.Year, dt2.Month, dt2.Day, dt2.Hour, dt2.Minute, dt2.Second, dt2.Millisecond  
/* Output (assuming first culture is en-US and second is fr-FR):  
    Year: 2008, Month: 1, Day: 8, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Year: 2008, Month: 8, Day: 1, Hour: 14, Minute: 50, Second: 50, Millisecond: 420  
Press any key to continue . . .  
 */  
```  
  
## <a name="example"></a><span data-ttu-id="b5993-114">範例</span><span class="sxs-lookup"><span data-stu-id="b5993-114">Example</span></span>  
 <span data-ttu-id="b5993-115">[!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b5993-115">[!code-cs[csProgGuideStrings#13](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-a-string-to-a-datetime_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5993-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5993-116">See Also</span></span>  
 [<span data-ttu-id="b5993-117">字串</span><span class="sxs-lookup"><span data-stu-id="b5993-117">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

