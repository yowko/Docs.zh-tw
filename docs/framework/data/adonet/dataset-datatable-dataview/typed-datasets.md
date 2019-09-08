---
title: 具類型資料集
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 7c8111e0e62a57b6745a5ea0387fc65a05839df8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785847"
---
# <a name="typed-datasets"></a><span data-ttu-id="503e4-102">具類型資料集</span><span class="sxs-lookup"><span data-stu-id="503e4-102">Typed DataSets</span></span>
<span data-ttu-id="503e4-103"><xref:System.Data.DataSet> 可透過弱型別變數，使用晚期繫結存取值，也可透過強型別變數存取資料。</span><span class="sxs-lookup"><span data-stu-id="503e4-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="503e4-104">您可以使用使用者易記名稱和強型別變數來存取**資料集**一部分的資料表和資料行。</span><span class="sxs-lookup"><span data-stu-id="503e4-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="503e4-105">具類型**資料集**是衍生自**資料集**的類別。</span><span class="sxs-lookup"><span data-stu-id="503e4-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="503e4-106">因此，它會繼承**資料集**的所有方法、事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="503e4-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="503e4-107">此外，具類型的**資料集**提供強型別方法、事件和屬性。</span><span class="sxs-lookup"><span data-stu-id="503e4-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="503e4-108">換句話說，您可以依照名稱存取資料表和資料行，而不需要使用集合架構的方法。</span><span class="sxs-lookup"><span data-stu-id="503e4-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="503e4-109">除了增強的程式碼可讀性之外，具類型的**資料集**也可讓 Visual Studio 的 .net 程式碼編輯器在您輸入時自動完成行。</span><span class="sxs-lookup"><span data-stu-id="503e4-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="503e4-110">此外，強型別**資料集**會在編譯時期提供值的存取權做為正確的類型。</span><span class="sxs-lookup"><span data-stu-id="503e4-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="503e4-111">使用強型別**資料集**時，在編譯器代碼而不是在執行時間時，會攔截到類型不符的錯誤。</span><span class="sxs-lookup"><span data-stu-id="503e4-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="503e4-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="503e4-112">In This Section</span></span>  
 [<span data-ttu-id="503e4-113">產生強型別資料集</span><span class="sxs-lookup"><span data-stu-id="503e4-113">Generating Strongly Typed DataSets</span></span>](generating-strongly-typed-datasets.md)  
 <span data-ttu-id="503e4-114">描述如何建立和使用強型別**資料集**。</span><span class="sxs-lookup"><span data-stu-id="503e4-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="503e4-115">註釋具類型資料集</span><span class="sxs-lookup"><span data-stu-id="503e4-115">Annotating Typed DataSets</span></span>](annotating-typed-datasets.md)  
 <span data-ttu-id="503e4-116">描述如何標注用來產生強型別**資料集**的 XML 架構定義語言（XSD）架構，以便在不改變基礎架構的情況下，為**DataSet**元素提供易記名稱。</span><span class="sxs-lookup"><span data-stu-id="503e4-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503e4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="503e4-117">See also</span></span>

- [<span data-ttu-id="503e4-118">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="503e4-118">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="503e4-119">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="503e4-119">ADO.NET Overview</span></span>](../ado-net-overview.md)
