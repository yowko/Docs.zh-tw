---
title: XML 資料型別轉換
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: b6e6f2c4b28e9220727bf0fe1a958a7b69111571
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202166"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="b200b-102">XML 資料型別轉換</span><span class="sxs-lookup"><span data-stu-id="b200b-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="b200b-103">在**XmlConvert**類別中找到的大部分方法都是用來轉換字串和強型別格式之間的資料。</span><span class="sxs-lookup"><span data-stu-id="b200b-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly typed formats.</span></span> <span data-ttu-id="b200b-104">這些方法都和地區設定無關。</span><span class="sxs-lookup"><span data-stu-id="b200b-104">Methods are locale independent.</span></span> <span data-ttu-id="b200b-105">也就是說，它們在進行轉換時並不會考慮任何地區設定的設定。</span><span class="sxs-lookup"><span data-stu-id="b200b-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="b200b-106">將字串讀成型別</span><span class="sxs-lookup"><span data-stu-id="b200b-106">Reading String as types</span></span>  
 <span data-ttu-id="b200b-107">下列範例會讀取一個字串，並將它轉換成 **DateTime** 型別。</span><span class="sxs-lookup"><span data-stu-id="b200b-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="b200b-108">假設有以下的 XML 輸入：</span><span class="sxs-lookup"><span data-stu-id="b200b-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="b200b-109">**輸入**</span><span class="sxs-lookup"><span data-stu-id="b200b-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="b200b-110">這個程式碼會將該字串轉換成 **DateTime** 格式：</span><span class="sxs-lookup"><span data-stu-id="b200b-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="b200b-111">將字串寫成型別</span><span class="sxs-lookup"><span data-stu-id="b200b-111">Writing Strings as types</span></span>  
 <span data-ttu-id="b200b-112">下列範例會讀取一個 **Int32**，並將它轉換成一個字串。</span><span class="sxs-lookup"><span data-stu-id="b200b-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="b200b-113">假設有以下的 XML 輸入：</span><span class="sxs-lookup"><span data-stu-id="b200b-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="b200b-114">**輸入**</span><span class="sxs-lookup"><span data-stu-id="b200b-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="b200b-115">這個程式碼會將 **Int32** 轉換成 **String**：</span><span class="sxs-lookup"><span data-stu-id="b200b-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="b200b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b200b-116">See also</span></span>

- [<span data-ttu-id="b200b-117">將字串轉換成 .NET Framework 資料型別</span><span class="sxs-lookup"><span data-stu-id="b200b-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="b200b-118">將 .NET Framework 型別轉換成字串</span><span class="sxs-lookup"><span data-stu-id="b200b-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
