---
title: 修改 XML 樹狀結構 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 8ec47e6d-2363-4694-be46-8d5ca4d15fc9
ms.openlocfilehash: 55e75762772a071b97eecb7d6d78e28c3002a179
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505715"
---
# <a name="modifying-xml-trees-linq-to-xml-c"></a><span data-ttu-id="ef920-102">修改 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef920-102">Modifying XML Trees (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ef920-103"> 是 XML 樹狀結構的記憶體中存放區。</span><span class="sxs-lookup"><span data-stu-id="ef920-103"> is an in-memory store for an XML tree.</span></span> <span data-ttu-id="ef920-104">在您從來源載入或剖析 XML 樹狀結構後，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會讓您就地修改該樹狀結構，然後序列化樹狀結構，以便將其儲存到檔案或傳送到遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="ef920-104">After you load or parse an XML tree from a source, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lets you modify that tree in place, and then serialize the tree, perhaps saving it to a file or sending it to a remote server.</span></span>  
  
 <span data-ttu-id="ef920-105">當您就地修改樹狀結構時，您可以使用特定方法，例如，<xref:System.Xml.Linq.XContainer.Add%2A>。</span><span class="sxs-lookup"><span data-stu-id="ef920-105">When you modify a tree in place, you use certain methods, such as <xref:System.Xml.Linq.XContainer.Add%2A>.</span></span>  
  
 <span data-ttu-id="ef920-106">不過，有另一個方法，就是使用功能結構來產生具有不同組織結構的新樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="ef920-106">However, there is another approach, which is to use functional construction to generate a new tree with a different shape.</span></span> <span data-ttu-id="ef920-107">根據您需要針對 XML 樹狀結構所進行之變更的類型，並根據樹狀結構的大小，這個方法可能更精簡也更容易開發。</span><span class="sxs-lookup"><span data-stu-id="ef920-107">Depending on the types of changes that you need to make to your XML tree, and depending on the size of the tree, this approach can be more robust and easier to develop.</span></span> <span data-ttu-id="ef920-108">本節中的第一個主題會比較這兩個方法。</span><span class="sxs-lookup"><span data-stu-id="ef920-108">The first topic in this section compares these two approaches.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef920-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="ef920-109">In This Section</span></span>  
  
|<span data-ttu-id="ef920-110">主題</span><span class="sxs-lookup"><span data-stu-id="ef920-110">Topic</span></span>|<span data-ttu-id="ef920-111">描述</span><span class="sxs-lookup"><span data-stu-id="ef920-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ef920-112">記憶體中 XML 樹狀結構修改與函數式建構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef920-112">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)|<span data-ttu-id="ef920-113">比較在記憶體中修改 XML 樹狀與功能結構。</span><span class="sxs-lookup"><span data-stu-id="ef920-113">Compares modifying an XML tree in memory to functional construction.</span></span>|  
|[<span data-ttu-id="ef920-114">將項目、屬性和節點加入至 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="ef920-114">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/adding-elements-attributes-and-nodes-to-an-xml-tree.md)|<span data-ttu-id="ef920-115">提供將項目、屬性或節點加入到 XML 樹狀的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ef920-115">Provides information about adding elements, attributes, or nodes to an XML tree.</span></span>|  
|[<span data-ttu-id="ef920-116">修改 XML 樹狀結構中的項目、屬性和節點</span><span class="sxs-lookup"><span data-stu-id="ef920-116">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|<span data-ttu-id="ef920-117">提供修改現有項目、屬性或節點的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ef920-117">Provides information about modifying existing elements, attributes, or nodes.</span></span>|  
|[<span data-ttu-id="ef920-118">從 XML 樹狀結構移除項目、屬性和節點 (C#)</span><span class="sxs-lookup"><span data-stu-id="ef920-118">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/removing-elements-attributes-and-nodes-from-an-xml-tree.md)|<span data-ttu-id="ef920-119">提供將項目、屬性或節點從 XML 樹狀移除的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ef920-119">Provides information about removing elements, attributes, or nodes from the XML tree.</span></span>|  
|[<span data-ttu-id="ef920-120">維護名稱/值組 (C#)</span><span class="sxs-lookup"><span data-stu-id="ef920-120">Maintaining Name/Value Pairs (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/maintaining-name-value-pairs.md)|<span data-ttu-id="ef920-121">描述如何維護妥善保存為成對名稱/值 (例如，組態資訊或全域設定) 的應用程式資訊。</span><span class="sxs-lookup"><span data-stu-id="ef920-121">Describes how to maintain application information that is best kept as name/value pairs, such as configuration information or global settings.</span></span>|  
|[<span data-ttu-id="ef920-122">如何：變更整個 XML 樹狀結構的命名空間 (C#)</span><span class="sxs-lookup"><span data-stu-id="ef920-122">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-change-the-namespace-for-an-entire-xml-tree.md)|<span data-ttu-id="ef920-123">顯示如何將 XML 樹狀從一個命名空間移到另一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef920-123">Shows how to move an XML tree from one namespace into another.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef920-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="ef920-124">See Also</span></span>

- [<span data-ttu-id="ef920-125">程式設計手冊 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef920-125">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
