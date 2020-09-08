---
title: 序列化時保留空白字元-LINQ to XML
description: 在序列化 XML 樹狀結構時，您可以使用各種方式來控制空白字元。
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d907e68a2df3905794b555954330f31b5e75655
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552157"
---
# <a name="preserve-white-space-while-serializing-linq-to-xml"></a><span data-ttu-id="83ece-103">將 (LINQ to XML 序列化時保留空白字元) </span><span class="sxs-lookup"><span data-stu-id="83ece-103">Preserve white space while serializing (LINQ to XML)</span></span>

<span data-ttu-id="83ece-104">本文描述如何在序列化 XML 樹狀結構時控制空白字元。</span><span class="sxs-lookup"><span data-stu-id="83ece-104">This article describes how to control white space when serializing an XML tree.</span></span>

<span data-ttu-id="83ece-105">常見的案例是讀取縮排的 XML、建立記憶體中的 XML 樹狀結構，而不含任何空白字元文位元組點 (也就是不保留空白字元) 、對 XML 進行某些作業，然後以縮排儲存 XML。</span><span class="sxs-lookup"><span data-stu-id="83ece-105">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="83ece-106">當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。</span><span class="sxs-lookup"><span data-stu-id="83ece-106">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="83ece-107">這是 LINQ to XML 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="83ece-107">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="83ece-108">其他常見案例為讀取與修改已經過刻意縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="83ece-108">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="83ece-109">您可能不想用任何方式變更這個縮排。</span><span class="sxs-lookup"><span data-stu-id="83ece-109">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="83ece-110">若要在 LINQ to XML 中這麼做，您可以在載入或剖析 XML 時保留空白字元，並且在序列化 XML 時停用格式設定。</span><span class="sxs-lookup"><span data-stu-id="83ece-110">To do this in LINQ to XML, you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>

## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="83ece-111">序列化 XML 樹狀結構之方法的空白字元行為</span><span class="sxs-lookup"><span data-stu-id="83ece-111">White-space behavior of methods that serialize XML trees</span></span>

<span data-ttu-id="83ece-112">下列 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 類別中的方法會序列化 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="83ece-112">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="83ece-113">您可以將 XML 樹狀結構序列化至檔案、<xref:System.IO.TextReader> 或 <xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="83ece-113">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="83ece-114">`ToString` 方法會序列化至字串。</span><span class="sxs-lookup"><span data-stu-id="83ece-114">The `ToString` method serializes to a string.</span></span>

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- [<span data-ttu-id="83ece-115">XElement.ToString()</span><span class="sxs-lookup"><span data-stu-id="83ece-115">XElement.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
- [<span data-ttu-id="83ece-116">XDocument.ToString()</span><span class="sxs-lookup"><span data-stu-id="83ece-116">XDocument.ToString()</span></span>](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)

<span data-ttu-id="83ece-117">如果方法未採用做 <xref:System.Xml.Linq.SaveOptions> 為引數，則此方法將會格式化 (縮排) 序列化的 XML。</span><span class="sxs-lookup"><span data-stu-id="83ece-117">If the method doesn't take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="83ece-118">在此情況下，會宣告 XML 樹狀結構中的所有有效空白字元。</span><span class="sxs-lookup"><span data-stu-id="83ece-118">In this case, all insignificant white space in the XML tree is discarded.</span></span>

<span data-ttu-id="83ece-119">如果此方法採用 <xref:System.Xml.Linq.SaveOptions> 當做引數，您就可以指定該方法不格式化 (縮排) 序列化的 XML。</span><span class="sxs-lookup"><span data-stu-id="83ece-119">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="83ece-120">在此情況下，會保留 XML 樹狀中的所有空白字元。</span><span class="sxs-lookup"><span data-stu-id="83ece-120">In this case, all white space in the XML tree is preserved.</span></span>
