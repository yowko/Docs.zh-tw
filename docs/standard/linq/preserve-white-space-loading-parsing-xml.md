---
title: 載入或剖析 XML 時保留空白字元 LINQ to XML
description: 您可以控制填入 XML 樹狀的 LINQ to XML 方法的空白字元行為。 例如，您可以移除記憶體中處理的縮排，或保持原狀。
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 783a1198f0b1754c690f04159860056a0fbadeb4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552164"
---
# <a name="preserve-white-space-while-loading-or-parsing-xml-linq-to-xml"></a><span data-ttu-id="b5868-104">載入或剖析 XML (LINQ to XML) 時保留空白字元</span><span class="sxs-lookup"><span data-stu-id="b5868-104">Preserve white space while loading or parsing XML (LINQ to XML)</span></span>

<span data-ttu-id="b5868-105">本文說明如何控制 LINQ to XML 的空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="b5868-105">This article describes how to control the white space behavior of LINQ to XML.</span></span>

<span data-ttu-id="b5868-106">常見的案例是讀取縮排的 XML、建立記憶體中的 XML 樹狀結構，而不含任何空白字元文位元組點 (也就是不保留空白字元) 、對 XML 進行某些作業，然後以縮排儲存 XML。</span><span class="sxs-lookup"><span data-stu-id="b5868-106">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="b5868-107">當您序列化具有格式的 XML 時，只會保留 XML 樹狀結構中的有效空白字元。</span><span class="sxs-lookup"><span data-stu-id="b5868-107">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="b5868-108">這是 LINQ to XML 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="b5868-108">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="b5868-109">其他常見案例為讀取與修改已經過刻意縮排的 XML。</span><span class="sxs-lookup"><span data-stu-id="b5868-109">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="b5868-110">您可能不想用任何方式變更這個縮排。</span><span class="sxs-lookup"><span data-stu-id="b5868-110">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="b5868-111">若要在 LINQ to XML 中這麼做，您可以在載入或剖析 XML 時保留空白字元，並且在序列化 XML 時停用格式設定。</span><span class="sxs-lookup"><span data-stu-id="b5868-111">To do this in LINQ to XML, you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>

<span data-ttu-id="b5868-112">本文描述填入 XML 樹狀結構之方法的空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="b5868-112">This article describes the white space behavior of methods that populate XML trees.</span></span> <span data-ttu-id="b5868-113">如需在序列化 XML 樹狀結構時控制空白字元的詳細資訊，請參閱在序列化 [時保留空白字元](preserve-white-space-serializing.md)。</span><span class="sxs-lookup"><span data-stu-id="b5868-113">For information about controlling white space when you serialize XML trees, see [Preserve white space while serializing](preserve-white-space-serializing.md).</span></span>

## <a name="behavior-of-methods-that-populate-xml-trees"></a><span data-ttu-id="b5868-114">填入 XML 樹狀結構之方法的行為</span><span class="sxs-lookup"><span data-stu-id="b5868-114">Behavior of methods that populate XML trees</span></span>

<span data-ttu-id="b5868-115">下列 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XDocument> 類別中的方法會填入 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="b5868-115">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes populate an XML tree.</span></span> <span data-ttu-id="b5868-116">您可以從檔案、<xref:System.IO.TextReader>、<xref:System.Xml.XmlReader> 或字串填入 XML 樹狀：</span><span class="sxs-lookup"><span data-stu-id="b5868-116">You can populate an XML tree from a file, a <xref:System.IO.TextReader>, an <xref:System.Xml.XmlReader>, or a string:</span></span>

- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>

<span data-ttu-id="b5868-117">如果方法未採用做 <xref:System.Xml.Linq.LoadOptions> 為引數，此方法將不會保留無意義的空白字元。</span><span class="sxs-lookup"><span data-stu-id="b5868-117">If the method doesn't take <xref:System.Xml.Linq.LoadOptions> as an argument, the method won't preserve insignificant white space.</span></span>

<span data-ttu-id="b5868-118">在大部分的情況下，如果此方法採用 <xref:System.Xml.Linq.LoadOptions> 當做引數，您可以選擇性地保留有效空白字元當做 XML 樹狀結構中的文字節點。</span><span class="sxs-lookup"><span data-stu-id="b5868-118">In most cases, if the method takes <xref:System.Xml.Linq.LoadOptions> as an argument, you can optionally preserve insignificant white space as text nodes in the XML tree.</span></span> <span data-ttu-id="b5868-119">不過，如果此方法是從 <xref:System.Xml.XmlReader> 載入 XML，<xref:System.Xml.XmlReader> 會決定是否要保留空白字元。</span><span class="sxs-lookup"><span data-stu-id="b5868-119">However, if the method is loading the XML from an <xref:System.Xml.XmlReader>, then the <xref:System.Xml.XmlReader> determines whether white space will be preserved or not.</span></span> <span data-ttu-id="b5868-120">設定 <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> 不會有任何作用。</span><span class="sxs-lookup"><span data-stu-id="b5868-120">Setting <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> will have no effect.</span></span>

<span data-ttu-id="b5868-121">利用這些方法，如果保留空白字元，會將有效的空白字元插入到 XML 樹狀結構中，當做 <xref:System.Xml.Linq.XText> 節點。</span><span class="sxs-lookup"><span data-stu-id="b5868-121">With these methods, if white space is preserved, insignificant white space is inserted into the XML tree as <xref:System.Xml.Linq.XText> nodes.</span></span> <span data-ttu-id="b5868-122">如果不保留空白字元，則不會插入文位元組點。</span><span class="sxs-lookup"><span data-stu-id="b5868-122">If white space isn't preserved, text nodes aren't inserted.</span></span>

<span data-ttu-id="b5868-123">您可以使用 <xref:System.Xml.XmlWriter> 來建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="b5868-123">You can create an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="b5868-124">寫入到 <xref:System.Xml.XmlWriter> 中的節點會填入樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="b5868-124">Nodes that are written to the <xref:System.Xml.XmlWriter> are populated in the tree.</span></span> <span data-ttu-id="b5868-125">不過，當您使用這個方法建置 XML 樹狀時，不管節點是否為空白字元，也不管空白字元是否有效，都會保留所有節點。</span><span class="sxs-lookup"><span data-stu-id="b5868-125">However, when you build an XML tree using this method, all nodes are preserved, regardless of whether the node is white space or not, or whether the white space is significant or not.</span></span>
