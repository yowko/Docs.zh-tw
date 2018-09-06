---
title: 具類型資料集
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 68721bcdbce6bf6d3279d6018ce6bc48d65c55a3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039802"
---
# <a name="typed-datasets"></a><span data-ttu-id="b6b4a-102">具類型資料集</span><span class="sxs-lookup"><span data-stu-id="b6b4a-102">Typed DataSets</span></span>
<span data-ttu-id="b6b4a-103"><xref:System.Data.DataSet> 可透過弱型別變數，使用晚期繫結存取值，也可透過強型別變數存取資料。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="b6b4a-104">資料表和資料行屬於**資料集**可以使用好記名稱和存取強型別變數。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="b6b4a-105">具型別**資料集**是衍生自類別**DataSet**。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="b6b4a-106">因此，所有方法、 事件和屬性的都繼承**資料集**。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="b6b4a-107">此外，具型別**資料集**提供強型別的方法、 事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="b6b4a-108">換句話說，您可以依照名稱存取資料表和資料行，而不需要使用集合架構的方法。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="b6b4a-109">除了更容易閱讀的程式碼，具型別**資料集**也可讓 Visual Studio.NET 程式碼編輯器，當您輸入時自動完成輸入行。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="b6b4a-110">此外，強型別**資料集**提供存取值為正確的類型，在編譯時期。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="b6b4a-111">使用強型別**資料集**，程式碼是編譯而不會在執行階段時攔截類型不符的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6b4a-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="b6b4a-112">In This Section</span></span>  
 [<span data-ttu-id="b6b4a-113">產生強型別資料集</span><span class="sxs-lookup"><span data-stu-id="b6b4a-113">Generating Strongly Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 <span data-ttu-id="b6b4a-114">描述如何建立和使用強型別**資料集**。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="b6b4a-115">註釋具類型資料集</span><span class="sxs-lookup"><span data-stu-id="b6b4a-115">Annotating Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 <span data-ttu-id="b6b4a-116">描述如何用來產生強類型的 XML 結構描述定義語言 (XSD) 結構描述加上註解**資料集**，以提供**DataSet**項目的易記名稱，而不需要變更基礎結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6b4a-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b4a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6b4a-117">See Also</span></span>  
 [<span data-ttu-id="b6b4a-118">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="b6b4a-118">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="b6b4a-119">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b6b4a-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
