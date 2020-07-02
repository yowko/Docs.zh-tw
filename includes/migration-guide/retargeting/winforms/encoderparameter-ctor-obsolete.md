---
ms.openlocfilehash: 4ad7c4c2781480c08ad4cf27e40de445b1c50671
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617146"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="4c97e-101">EncoderParameter ctor 已淘汰</span><span class="sxs-lookup"><span data-stu-id="4c97e-101">EncoderParameter ctor is obsolete</span></span>

#### <a name="details"></a><span data-ttu-id="4c97e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4c97e-102">Details</span></span>

<span data-ttu-id="4c97e-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 建構函式現在已淘汰，如果使用，就會產生建置警告。</span><span class="sxs-lookup"><span data-stu-id="4c97e-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4c97e-104">建議</span><span class="sxs-lookup"><span data-stu-id="4c97e-104">Suggestion</span></span>

<span data-ttu-id="4c97e-105">雖然 <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 建構函式會繼續運作，但應改用下列建構函式，以避免使用 .NET Framework 4.5 工具重新編譯程式碼時出現已淘汰的建置警告：<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>。</span><span class="sxs-lookup"><span data-stu-id="4c97e-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>

| <span data-ttu-id="4c97e-106">名稱</span><span class="sxs-lookup"><span data-stu-id="4c97e-106">Name</span></span>    | <span data-ttu-id="4c97e-107">值</span><span class="sxs-lookup"><span data-stu-id="4c97e-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4c97e-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="4c97e-108">Scope</span></span>   | <span data-ttu-id="4c97e-109">Minor</span><span class="sxs-lookup"><span data-stu-id="4c97e-109">Minor</span></span>       |
| <span data-ttu-id="4c97e-110">版本</span><span class="sxs-lookup"><span data-stu-id="4c97e-110">Version</span></span> | <span data-ttu-id="4c97e-111">4.5</span><span class="sxs-lookup"><span data-stu-id="4c97e-111">4.5</span></span>         |
| <span data-ttu-id="4c97e-112">類型</span><span class="sxs-lookup"><span data-stu-id="4c97e-112">Type</span></span>    | <span data-ttu-id="4c97e-113">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="4c97e-113">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4c97e-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4c97e-114">Affected APIs</span></span>

- <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>
