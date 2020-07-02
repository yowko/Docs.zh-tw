---
ms.openlocfilehash: 5d5423d18091545ad9d50325900f5a9a4fff6dd9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621955"
---
### <a name="fixed-a-hang-when-listbox-contains-duplicate-value-types"></a><span data-ttu-id="68e3a-101">已修正當 ListBox 包含重複實值型別時的停止回應問題</span><span class="sxs-lookup"><span data-stu-id="68e3a-101">Fixed a hang when ListBox contains duplicate value-types</span></span>

#### <a name="details"></a><span data-ttu-id="68e3a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="68e3a-102">Details</span></span>

<span data-ttu-id="68e3a-103">已修正下列問題：當虛擬化 <xref:System.Windows.Controls.ItemsControl> 的項目集合包含重複實值型別物件時，其在捲動期間會停止回應。</span><span class="sxs-lookup"><span data-stu-id="68e3a-103">Fixed a problem where a virtualizing<xref:System.Windows.Controls.ItemsControl> can hang during scrolling when its Items collection contains duplicate value-typed objects.</span></span>

| <span data-ttu-id="68e3a-104">名稱</span><span class="sxs-lookup"><span data-stu-id="68e3a-104">Name</span></span>    | <span data-ttu-id="68e3a-105">值</span><span class="sxs-lookup"><span data-stu-id="68e3a-105">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="68e3a-106">影響範圍</span><span class="sxs-lookup"><span data-stu-id="68e3a-106">Scope</span></span>   |<span data-ttu-id="68e3a-107">主要</span><span class="sxs-lookup"><span data-stu-id="68e3a-107">Major</span></span>|
|<span data-ttu-id="68e3a-108">版本</span><span class="sxs-lookup"><span data-stu-id="68e3a-108">Version</span></span>|<span data-ttu-id="68e3a-109">4.8</span><span class="sxs-lookup"><span data-stu-id="68e3a-109">4.8</span></span>|
|<span data-ttu-id="68e3a-110">類型</span><span class="sxs-lookup"><span data-stu-id="68e3a-110">Type</span></span>|<span data-ttu-id="68e3a-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="68e3a-111">Runtime</span></span>|
