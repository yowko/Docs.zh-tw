---
title: "將字串轉換成 .NET Framework 資料型別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce594234e601cd8feb4723bbc383db9e3ed40522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="2df18-102">將字串轉換成 .NET Framework 資料型別</span><span class="sxs-lookup"><span data-stu-id="2df18-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="2df18-103">如果您想要將字串轉換為.NET Framework 資料型別，使用**XmlConvert**符合應用程式需求的方法。</span><span class="sxs-lookup"><span data-stu-id="2df18-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="2df18-104">如需所有使用中的轉換方法的清單**XmlConvert**類別，請參閱<xref:System.Xml.XmlConvert>。</span><span class="sxs-lookup"><span data-stu-id="2df18-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="2df18-105">傳回的字串**ToString**方法是傳入資料的字串版本。</span><span class="sxs-lookup"><span data-stu-id="2df18-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="2df18-106">此外，有幾種轉換使用的.NET Framework 類型**XmlConvert**類別，但它們不會使用中的方法**System.Convert**類別。</span><span class="sxs-lookup"><span data-stu-id="2df18-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="2df18-107">**XmlConvert**類別遵循的 XML 結構描述 (XSD) 資料型別規格，並具有的資料類型， **XmlConvert**可以對應至。</span><span class="sxs-lookup"><span data-stu-id="2df18-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="2df18-108">下列表格列出使用 XML 結構描述 (XSD) 資料型別對應所傳回的 .NET Framework 資料型別和字串型別。</span><span class="sxs-lookup"><span data-stu-id="2df18-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="2df18-109">這些.NET Framework 型別無法使用處理**System.Convert**。</span><span class="sxs-lookup"><span data-stu-id="2df18-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="2df18-110">.NET Framework 類型</span><span class="sxs-lookup"><span data-stu-id="2df18-110">.NET Framework type</span></span>|<span data-ttu-id="2df18-111">傳回的字串</span><span class="sxs-lookup"><span data-stu-id="2df18-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="2df18-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="2df18-112">Boolean</span></span>|<span data-ttu-id="2df18-113">"true"、"false"</span><span class="sxs-lookup"><span data-stu-id="2df18-113">"true", "false"</span></span>|  
|<span data-ttu-id="2df18-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="2df18-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="2df18-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="2df18-115">"INF"</span></span>|  
|<span data-ttu-id="2df18-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="2df18-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="2df18-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="2df18-117">"-INF"</span></span>|  
|<span data-ttu-id="2df18-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="2df18-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="2df18-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="2df18-119">"INF"</span></span>|  
|<span data-ttu-id="2df18-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="2df18-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="2df18-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="2df18-121">"-INF"</span></span>|  
|<span data-ttu-id="2df18-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="2df18-122">DateTime</span></span>|<span data-ttu-id="2df18-123">格式為 "yyyy-MM-ddTHH:mm:sszzzzzz" 及其子集。</span><span class="sxs-lookup"><span data-stu-id="2df18-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="2df18-124">Timespan</span><span class="sxs-lookup"><span data-stu-id="2df18-124">Timespan</span></span>|<span data-ttu-id="2df18-125">格式為 PnYnMnTnHnMnS，即 `P2Y10M15DT10H30M20S` 代表期間為 2 年 10 個月 15 天 10 小時 30 分鐘 20 秒。</span><span class="sxs-lookup"><span data-stu-id="2df18-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="2df18-126">如果任何.NET Framework 類型轉換表所列的字串，使用**ToString**方法，傳回的字串不是基底型別，而 XML 結構描述 (XSD) 字串型別。</span><span class="sxs-lookup"><span data-stu-id="2df18-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="2df18-127">**DateTime**和**Timespan**數值型別的差別在於**DateTime**表示時間的瞬間而**TimeSpan**表示時間間隔。</span><span class="sxs-lookup"><span data-stu-id="2df18-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="2df18-128">**DateTime**和**Timespan** XML 結構描述 (XSD) 資料型別規格中指定的格式。</span><span class="sxs-lookup"><span data-stu-id="2df18-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="2df18-129">例如: </span><span class="sxs-lookup"><span data-stu-id="2df18-129">For example:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 <span data-ttu-id="2df18-130">**輸出**</span><span class="sxs-lookup"><span data-stu-id="2df18-130">**Output**</span></span>  
  
 <span data-ttu-id="2df18-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="2df18-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="2df18-132">下列程式碼會將整數轉換成字串：</span><span class="sxs-lookup"><span data-stu-id="2df18-132">The following code converts an integer to a string:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 <span data-ttu-id="2df18-133">**輸出**</span><span class="sxs-lookup"><span data-stu-id="2df18-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="2df18-134">不過，如果您想要轉換的字串**布林**，**單一**，或**Double**，就會傳回.NET Framework 型別不是使用時，傳回的類型相同**System.Convert**類別。</span><span class="sxs-lookup"><span data-stu-id="2df18-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="2df18-135">字串轉成 Boolean</span><span class="sxs-lookup"><span data-stu-id="2df18-135">String to Boolean</span></span>  
 <span data-ttu-id="2df18-136">下表顯示當字串轉換成指定的輸入字串，請產生哪些型別**布林**使用**ToBoolean**方法。</span><span class="sxs-lookup"><span data-stu-id="2df18-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="2df18-137">有效的字串輸入參數</span><span class="sxs-lookup"><span data-stu-id="2df18-137">Valid string input parameter</span></span>|<span data-ttu-id="2df18-138">.NET Framework 輸出型別</span><span class="sxs-lookup"><span data-stu-id="2df18-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="2df18-139">"true"</span><span class="sxs-lookup"><span data-stu-id="2df18-139">"true"</span></span>|<span data-ttu-id="2df18-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="2df18-140">Boolean.True</span></span>|  
|<span data-ttu-id="2df18-141">"1"</span><span class="sxs-lookup"><span data-stu-id="2df18-141">"1"</span></span>|<span data-ttu-id="2df18-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="2df18-142">Boolean.True</span></span>|  
|<span data-ttu-id="2df18-143">"false"</span><span class="sxs-lookup"><span data-stu-id="2df18-143">"false"</span></span>|<span data-ttu-id="2df18-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="2df18-144">Boolean.False</span></span>|  
|<span data-ttu-id="2df18-145">"0"</span><span class="sxs-lookup"><span data-stu-id="2df18-145">"0"</span></span>|<span data-ttu-id="2df18-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="2df18-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="2df18-147">例如，假設有以下的 XML：</span><span class="sxs-lookup"><span data-stu-id="2df18-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="2df18-148">**輸入**</span><span class="sxs-lookup"><span data-stu-id="2df18-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 <span data-ttu-id="2df18-149">下列程式碼，同時可以理解和**bvalue**是**System.Boolean.True**:</span><span class="sxs-lookup"><span data-stu-id="2df18-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="2df18-150">字串轉成 Single</span><span class="sxs-lookup"><span data-stu-id="2df18-150">String to Single</span></span>  
 <span data-ttu-id="2df18-151">下表顯示當字串轉換成指定的輸入字串，請產生哪些型別**單一**使用**ToSingle**方法。</span><span class="sxs-lookup"><span data-stu-id="2df18-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="2df18-152">有效的字串輸入參數</span><span class="sxs-lookup"><span data-stu-id="2df18-152">Valid string input parameter</span></span>|<span data-ttu-id="2df18-153">.NET Framework 輸出型別</span><span class="sxs-lookup"><span data-stu-id="2df18-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="2df18-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="2df18-154">"INF"</span></span>|<span data-ttu-id="2df18-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="2df18-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="2df18-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="2df18-156">"-INF"</span></span>|<span data-ttu-id="2df18-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="2df18-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="2df18-158">字串轉成 Double</span><span class="sxs-lookup"><span data-stu-id="2df18-158">String to Double</span></span>  
 <span data-ttu-id="2df18-159">下表顯示當字串轉換成指定的輸入字串，請產生哪些型別**單一**使用**ToDouble**方法。</span><span class="sxs-lookup"><span data-stu-id="2df18-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="2df18-160">有效的字串輸入參數</span><span class="sxs-lookup"><span data-stu-id="2df18-160">Valid string input parameter</span></span>|<span data-ttu-id="2df18-161">.NET Framework 輸出型別</span><span class="sxs-lookup"><span data-stu-id="2df18-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="2df18-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="2df18-162">"INF"</span></span>|<span data-ttu-id="2df18-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="2df18-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="2df18-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="2df18-164">"-INF"</span></span>|<span data-ttu-id="2df18-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="2df18-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="2df18-166">下列程式碼寫入 `<Infinity>INF</Infinity>`：</span><span class="sxs-lookup"><span data-stu-id="2df18-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="2df18-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2df18-167">See Also</span></span>  
 [<span data-ttu-id="2df18-168">XML 資料型別轉換</span><span class="sxs-lookup"><span data-stu-id="2df18-168">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [<span data-ttu-id="2df18-169">將.NET Framework 型別轉換為字串</span><span class="sxs-lookup"><span data-stu-id="2df18-169">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
