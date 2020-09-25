---
title: 具類型資料集
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 4648d49b1d7419d61a3a000404f42e0d02d25786
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198440"
---
# <a name="typed-datasets"></a><span data-ttu-id="b2236-102">具類型資料集</span><span class="sxs-lookup"><span data-stu-id="b2236-102">Typed DataSets</span></span>

<span data-ttu-id="b2236-103"><xref:System.Data.DataSet> 可透過弱型別變數，使用晚期繫結存取值，也可透過強型別變數存取資料。</span><span class="sxs-lookup"><span data-stu-id="b2236-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="b2236-104">您可以使用易記的名稱和強型別變數來存取屬於 **資料集** 一部分的資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="b2236-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="b2236-105">具類型 **資料集** 是衍生自 **資料集**的類別。</span><span class="sxs-lookup"><span data-stu-id="b2236-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="b2236-106">因此，它會繼承 **資料集**的所有方法、事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="b2236-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="b2236-107">此外，具類型的 **資料集會** 提供強型別方法、事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="b2236-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="b2236-108">換句話說，您可以依照名稱存取資料表和資料行，而不需要使用集合架構的方法。</span><span class="sxs-lookup"><span data-stu-id="b2236-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="b2236-109">除了改良的程式碼可讀性之外，具類型的 **資料集** 也可讓 Visual Studio .NET 程式碼編輯器在您輸入時自動完成行。</span><span class="sxs-lookup"><span data-stu-id="b2236-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="b2236-110">此外，強型別 **資料集** 可讓您在編譯時期，以正確的型別來存取值。</span><span class="sxs-lookup"><span data-stu-id="b2236-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="b2236-111">使用強型別 **資料集**時，在編譯器代碼時（而不是在執行時間），會攔截到類型不符的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b2236-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2236-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="b2236-112">In This Section</span></span>  

 [<span data-ttu-id="b2236-113">產生強類型資料集</span><span class="sxs-lookup"><span data-stu-id="b2236-113">Generating Strongly Typed DataSets</span></span>](generating-strongly-typed-datasets.md)  
 <span data-ttu-id="b2236-114">描述如何建立和使用強型別 **資料集**。</span><span class="sxs-lookup"><span data-stu-id="b2236-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="b2236-115">註釋具類型資料集</span><span class="sxs-lookup"><span data-stu-id="b2236-115">Annotating Typed DataSets</span></span>](annotating-typed-datasets.md)  
 <span data-ttu-id="b2236-116">描述如何標注 XML 架構定義語言 (XSD) 架構，用來產生強型別 **資料集**，以便在不改變基礎架構的情況下，提供 **資料集** 元素的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="b2236-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2236-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2236-117">See also</span></span>

- [<span data-ttu-id="b2236-118">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="b2236-118">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="b2236-119">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="b2236-119">[ADO.NET Overview](../ado-net-overview.md)</span></span>
