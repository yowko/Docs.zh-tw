---
title: 序列化時保留空白字元
description: 瞭解如何在使用 System.xml.linq.xelement> 和 XDocument 類別中的方法序列化 XML 樹狀結構時控制空白字元。
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 01e68671e2fde1a2b5b1d0bc429841077ba0205f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303409"
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="3d8f1-103">序列化時保留空白字元</span><span class="sxs-lookup"><span data-stu-id="3d8f1-103">Preserving White Space While Serializing</span></span>
<span data-ttu-id="3d8f1-104">本主題描述如何在序列化 XML 樹狀結構時控制空白字元。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-104">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="3d8f1-105">常見的案例為讀取縮排的 XML、建立沒有任何空白字元文字節點 (也就是不保留空白字元) 的記憶體中 XML 樹狀結構、在 XML 上執行某些作業，然後儲存包含縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-105">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="3d8f1-106">當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="3d8f1-107">這是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-107">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="3d8f1-108">其他常見案例為讀取與修改已經過刻意縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="3d8f1-109">您可能不想用任何方式變更這個縮排。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="3d8f1-110">在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，如果您在載入或剖析 XML 時保留空白字元，並在序列化 XML 時停用格式化，就可以達到這個效果。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-110">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="3d8f1-111">將 XML 樹狀結構序列化之方法的空白字元行為</span><span class="sxs-lookup"><span data-stu-id="3d8f1-111">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="3d8f1-112">下列 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 類別中的方法會序列化 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-112">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="3d8f1-113">您可以將 XML 樹狀結構序列化至檔案、<xref:System.IO.TextReader> 或 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-113">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="3d8f1-114">`ToString` 方法會序列化至字串。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-114">The `ToString` method serializes to a string.</span></span>  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [<span data-ttu-id="3d8f1-115">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="3d8f1-115">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [<span data-ttu-id="3d8f1-116">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="3d8f1-116">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 <span data-ttu-id="3d8f1-117">如果此方法不採用 <xref:System.Xml.Linq.SaveOptions> 當做引數，該方法將會格式化 (縮排) 序列化的 XML。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-117">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="3d8f1-118">在此情況下，會宣告 XML 樹狀結構中的所有有效空白字元。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-118">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="3d8f1-119">如果此方法採用 <xref:System.Xml.Linq.SaveOptions> 當做引數，您就可以指定該方法不格式化 (縮排) 序列化的 XML。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-119">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="3d8f1-120">在此情況下，會保留 XML 樹狀中的所有空白字元。</span><span class="sxs-lookup"><span data-stu-id="3d8f1-120">In this case, all white space in the XML tree is preserved.</span></span>  
