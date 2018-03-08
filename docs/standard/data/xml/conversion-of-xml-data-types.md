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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d18b69c2d5baeac77cbdf45bebd6f0c9d5c94d9f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="5172b-102">XML 資料型別轉換</span><span class="sxs-lookup"><span data-stu-id="5172b-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="5172b-103">大多數在 **XmlConvert** 類別中的方法都是用來轉換字串和強型別格式間的資料。</span><span class="sxs-lookup"><span data-stu-id="5172b-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="5172b-104">這些方法都和地區設定無關。</span><span class="sxs-lookup"><span data-stu-id="5172b-104">Methods are locale independent.</span></span> <span data-ttu-id="5172b-105">也就是說，它們在進行轉換時並不會考慮任何地區設定的設定。</span><span class="sxs-lookup"><span data-stu-id="5172b-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="5172b-106">將字串讀成型別</span><span class="sxs-lookup"><span data-stu-id="5172b-106">Reading String as types</span></span>  
 <span data-ttu-id="5172b-107">下列範例會讀取一個字串，並將它轉換成 **DateTime** 型別。</span><span class="sxs-lookup"><span data-stu-id="5172b-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="5172b-108">假設有以下的 XML 輸入：</span><span class="sxs-lookup"><span data-stu-id="5172b-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="5172b-109">**輸入**</span><span class="sxs-lookup"><span data-stu-id="5172b-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="5172b-110">這個程式碼會將該字串轉換成 **DateTime** 格式：</span><span class="sxs-lookup"><span data-stu-id="5172b-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="5172b-111">將字串寫成型別</span><span class="sxs-lookup"><span data-stu-id="5172b-111">Writing Strings as types</span></span>  
 <span data-ttu-id="5172b-112">下列範例會讀取一個 **Int32**，並將它轉換成一個字串。</span><span class="sxs-lookup"><span data-stu-id="5172b-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="5172b-113">假設有以下的 XML 輸入：</span><span class="sxs-lookup"><span data-stu-id="5172b-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="5172b-114">**輸入**</span><span class="sxs-lookup"><span data-stu-id="5172b-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="5172b-115">這個程式碼會將 **Int32** 轉換成 **String**：</span><span class="sxs-lookup"><span data-stu-id="5172b-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="5172b-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="5172b-116">See Also</span></span>  
 [<span data-ttu-id="5172b-117">將字串轉換成 .NET Framework 資料類型</span><span class="sxs-lookup"><span data-stu-id="5172b-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [<span data-ttu-id="5172b-118">將 .NET Framework 類型轉換成字串</span><span class="sxs-lookup"><span data-stu-id="5172b-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
