---
ms.openlocfilehash: f123f37d3f1be7d5b6805ac58529c1872a81f20b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619953"
---
### <a name="compiler-support-for-type-forwarding-when-multi-targeting-mscorlib"></a><span data-ttu-id="ef5e0-101">編譯器支援多目標 mscorlib 時的類型轉送</span><span class="sxs-lookup"><span data-stu-id="ef5e0-101">Compiler support for type forwarding when multi-targeting mscorlib</span></span>

#### <a name="details"></a><span data-ttu-id="ef5e0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ef5e0-102">Details</span></span>

<span data-ttu-id="ef5e0-103">新的 CodeDOM 功能可讓編譯器針對設為目標的 mscorlib.dll 版本 (而非 .NET Framework 4.5 版的 mscorlib.dll) 進行編譯。</span><span class="sxs-lookup"><span data-stu-id="ef5e0-103">A new CodeDOM feature allows a compiler to compile against the targeted version of mscorlib.dll instead of the .NET Framework 4.5 version of mscorlib.dll.</span></span>

| <span data-ttu-id="ef5e0-104">名稱</span><span class="sxs-lookup"><span data-stu-id="ef5e0-104">Name</span></span>    | <span data-ttu-id="ef5e0-105">值</span><span class="sxs-lookup"><span data-stu-id="ef5e0-105">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ef5e0-106">影響範圍</span><span class="sxs-lookup"><span data-stu-id="ef5e0-106">Scope</span></span>   |<span data-ttu-id="ef5e0-107">Edge</span><span class="sxs-lookup"><span data-stu-id="ef5e0-107">Edge</span></span>|
|<span data-ttu-id="ef5e0-108">版本</span><span class="sxs-lookup"><span data-stu-id="ef5e0-108">Version</span></span>|<span data-ttu-id="ef5e0-109">4.5</span><span class="sxs-lookup"><span data-stu-id="ef5e0-109">4.5</span></span>|
|<span data-ttu-id="ef5e0-110">類型</span><span class="sxs-lookup"><span data-stu-id="ef5e0-110">Type</span></span>|<span data-ttu-id="ef5e0-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="ef5e0-111">Runtime</span></span>|
