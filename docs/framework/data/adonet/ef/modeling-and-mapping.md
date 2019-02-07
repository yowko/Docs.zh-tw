---
title: 建立模型和對應
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 847d518710b21df714343b541401ff7fc8443fb3
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828302"
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="48961-102">建立模型和對應</span><span class="sxs-lookup"><span data-stu-id="48961-102">Modeling and Mapping</span></span>
<span data-ttu-id="48961-103">在 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 中，您可以使用應用程式最適合的方式來定義概念模型、儲存體模型，以及兩者間的對應。</span><span class="sxs-lookup"><span data-stu-id="48961-103">In the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="48961-104">在 Visual Studio 中的實體資料模型工具可讓您建立。[edmx 檔案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))從資料庫或圖形模型，然後更新該檔案在資料庫或模型變更時。</span><span class="sxs-lookup"><span data-stu-id="48961-104">The Entity Data Model Tools in Visual Studio allow you to create an .[edmx file](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="48961-105">從 Entity Framework 4.1 開始，您也可以使用 Code First 開發透過程式設計方式建立模型。</span><span class="sxs-lookup"><span data-stu-id="48961-105">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="48961-106">Code First 開發有兩種不同的方案。</span><span class="sxs-lookup"><span data-stu-id="48961-106">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="48961-107">在這兩種情況下，開發人員透過編碼 .NET Framework 類別定義建立模型，然後選擇性地使用資料註解或 Fluent 應用程式開發介面指定其他對應或組態。</span><span class="sxs-lookup"><span data-stu-id="48961-107">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="48961-108">如需詳細資訊，請參閱 <<c0> [ 建立與對應概念模型](https://go.microsoft.com/fwlink/?LinkId=235016)。</span><span class="sxs-lookup"><span data-stu-id="48961-108">For more information, see [Creating and Mapping a Conceptual Model](https://go.microsoft.com/fwlink/?LinkId=235016).</span></span>  
  
 <span data-ttu-id="48961-109">您也可以使用 EDM 產生器隨附[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="48961-109">You can also use the EDM Generator, which is included with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="48961-110">EdmGen.exe 可從現有的資料來源產生 .csdl、.ssdl 和 .msl 檔。</span><span class="sxs-lookup"><span data-stu-id="48961-110">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="48961-111">您也可以手動建立模型和對應內容。</span><span class="sxs-lookup"><span data-stu-id="48961-111">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="48961-112">如需詳細資訊，請參閱 < [EDM 產生器 (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="48961-112">For more information, see [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span></span>
