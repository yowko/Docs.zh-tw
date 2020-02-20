---
title: 建立模型和對應
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: e70411bb9c9797ee348aeef055c9af20ea092ae3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450592"
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="398d0-102">建立模型和對應</span><span class="sxs-lookup"><span data-stu-id="398d0-102">Modeling and Mapping</span></span>
<span data-ttu-id="398d0-103">在 Entity Framework 中，您可以定義概念模型、儲存體模型，以及這兩者之間的對應，這兩種方式最適合您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="398d0-103">In the Entity Framework, you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="398d0-104">Visual Studio 中的實體資料模型工具可讓您建立。來自資料庫或圖形化模型的[edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))檔案，然後在資料庫或模型變更時更新該檔案。</span><span class="sxs-lookup"><span data-stu-id="398d0-104">The Entity Data Model Tools in Visual Studio allow you to create an .[edmx file](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="398d0-105">從 Entity Framework 4.1 開始，您也可以使用 Code First 開發透過程式設計方式建立模型。</span><span class="sxs-lookup"><span data-stu-id="398d0-105">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="398d0-106">Code First 開發有兩種不同的方案。</span><span class="sxs-lookup"><span data-stu-id="398d0-106">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="398d0-107">在這兩種情況下，開發人員透過編碼 .NET Framework 類別定義建立模型，然後選擇性地使用資料註解或 Fluent 應用程式開發介面指定其他對應或組態。</span><span class="sxs-lookup"><span data-stu-id="398d0-107">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="398d0-108">如需詳細資訊，請參閱[建立模型](/ef/ef6/modeling/)。</span><span class="sxs-lookup"><span data-stu-id="398d0-108">For more information, see [Creating a Model](/ef/ef6/modeling/).</span></span>  
  
 <span data-ttu-id="398d0-109">您也可以使用包含在 .NET Framework 中的 EDM 產生器。</span><span class="sxs-lookup"><span data-stu-id="398d0-109">You can also use the EDM Generator, which is included with the .NET Framework.</span></span> <span data-ttu-id="398d0-110">EdmGen.exe 可從現有的資料來源產生 .csdl、.ssdl 和 .msl 檔。</span><span class="sxs-lookup"><span data-stu-id="398d0-110">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="398d0-111">您也可以手動建立模型和對應內容。</span><span class="sxs-lookup"><span data-stu-id="398d0-111">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="398d0-112">如需詳細資訊，請參閱 EDM 產生器[（edmgen.exe .exe）](edm-generator-edmgen-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="398d0-112">For more information, see [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md).</span></span>
