---
title: XML 資料型別轉換
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cec2b85c55871c8a21a74e79cfcdd041fa063bec
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45664575"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="91090-102">XML 資料型別轉換</span><span class="sxs-lookup"><span data-stu-id="91090-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="91090-103">大多數在 **XmlConvert** 類別中的方法都是用來轉換字串和強型別格式間的資料。</span><span class="sxs-lookup"><span data-stu-id="91090-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="91090-104">這些方法都和地區設定無關。</span><span class="sxs-lookup"><span data-stu-id="91090-104">Methods are locale independent.</span></span> <span data-ttu-id="91090-105">也就是說，它們在進行轉換時並不會考慮任何地區設定的設定。</span><span class="sxs-lookup"><span data-stu-id="91090-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="91090-106">將字串讀成型別</span><span class="sxs-lookup"><span data-stu-id="91090-106">Reading String as types</span></span>  
 <span data-ttu-id="91090-107">下列範例會讀取一個字串，並將它轉換成 **DateTime** 型別。</span><span class="sxs-lookup"><span data-stu-id="91090-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="91090-108">假設有以下的 XML 輸入：</span><span class="sxs-lookup"><span data-stu-id="91090-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="91090-109">**輸入**</span><span class="sxs-lookup"><span data-stu-id="91090-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="91090-110">這個程式碼會將該字串轉換成 **DateTime** 格式：</span><span class="sxs-lookup"><span data-stu-id="91090-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="91090-111">將字串寫成型別</span><span class="sxs-lookup"><span data-stu-id="91090-111">Writing Strings as types</span></span>  
 <span data-ttu-id="91090-112">下列範例會讀取一個 **Int32**，並將它轉換成一個字串。</span><span class="sxs-lookup"><span data-stu-id="91090-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="91090-113">假設有以下的 XML 輸入：</span><span class="sxs-lookup"><span data-stu-id="91090-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="91090-114">**輸入**</span><span class="sxs-lookup"><span data-stu-id="91090-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="91090-115">這個程式碼會將 **Int32** 轉換成 **String**：</span><span class="sxs-lookup"><span data-stu-id="91090-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="91090-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91090-116">See also</span></span>

- [<span data-ttu-id="91090-117">將字串轉換成 .NET Framework 資料類型</span><span class="sxs-lookup"><span data-stu-id="91090-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
- [<span data-ttu-id="91090-118">將 .NET Framework 類型轉換成字串</span><span class="sxs-lookup"><span data-stu-id="91090-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
