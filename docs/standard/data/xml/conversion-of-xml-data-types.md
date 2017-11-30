---
title: "XML 資料型別轉換"
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
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="1450b-102">XML 資料型別轉換</span><span class="sxs-lookup"><span data-stu-id="1450b-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="1450b-103">大部分的方法中找到**XmlConvert**類別用於字串和強型別格式之間轉換資料。</span><span class="sxs-lookup"><span data-stu-id="1450b-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="1450b-104">這些方法都和地區設定無關。</span><span class="sxs-lookup"><span data-stu-id="1450b-104">Methods are locale independent.</span></span> <span data-ttu-id="1450b-105">也就是說，它們在進行轉換時並不會考慮任何地區設定的設定。</span><span class="sxs-lookup"><span data-stu-id="1450b-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="1450b-106">將字串讀成型別</span><span class="sxs-lookup"><span data-stu-id="1450b-106">Reading String as types</span></span>  
 <span data-ttu-id="1450b-107">下列範例會讀取字串並轉換成**DateTime**型別。</span><span class="sxs-lookup"><span data-stu-id="1450b-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="1450b-108">假設有以下的 XML 輸入：</span><span class="sxs-lookup"><span data-stu-id="1450b-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="1450b-109">**輸入**</span><span class="sxs-lookup"><span data-stu-id="1450b-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="1450b-110">此程式碼將字串轉換成**DateTime**格式：</span><span class="sxs-lookup"><span data-stu-id="1450b-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="1450b-111">將字串寫成型別</span><span class="sxs-lookup"><span data-stu-id="1450b-111">Writing Strings as types</span></span>  
 <span data-ttu-id="1450b-112">下列範例會讀取**Int32**並將它轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="1450b-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="1450b-113">假設有以下的 XML 輸入：</span><span class="sxs-lookup"><span data-stu-id="1450b-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="1450b-114">**輸入**</span><span class="sxs-lookup"><span data-stu-id="1450b-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="1450b-115">此程式碼將轉換**Int32**到**字串**:</span><span class="sxs-lookup"><span data-stu-id="1450b-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="1450b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1450b-116">See Also</span></span>  
 [<span data-ttu-id="1450b-117">將字串轉換為.NET Framework 資料型別</span><span class="sxs-lookup"><span data-stu-id="1450b-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [<span data-ttu-id="1450b-118">將.NET Framework 型別轉換為字串</span><span class="sxs-lookup"><span data-stu-id="1450b-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
