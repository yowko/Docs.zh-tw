---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774315"
---
### <a name="encoderparameter-ctor-is-obsolete"></a><span data-ttu-id="8e940-101">EncoderParameter ctor 已淘汰</span><span class="sxs-lookup"><span data-stu-id="8e940-101">EncoderParameter ctor is obsolete</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8e940-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8e940-102">Details</span></span>|<span data-ttu-id="8e940-103"><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 建構函式現在已淘汰，如果使用，就會產生建置警告。</span><span class="sxs-lookup"><span data-stu-id="8e940-103">The <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> constructor is obsolete now and will introduce build warnings if used.</span></span>|
|<span data-ttu-id="8e940-104">建議</span><span class="sxs-lookup"><span data-stu-id="8e940-104">Suggestion</span></span>|<span data-ttu-id="8e940-105">雖然 <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> 建構函式會繼續運作，但應改用下列建構函式，以避免使用 .NET Framework 4.5 工具重新編譯程式碼時出現已淘汰的建置警告：<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>。</span><span class="sxs-lookup"><span data-stu-id="8e940-105">Although the <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>constructor will continue to work, the following constructor should be used instead to avoid the obsolete build warning when re-compiling code with .NET Framework  4.5 tools: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.</span></span>|
|<span data-ttu-id="8e940-106">範圍</span><span class="sxs-lookup"><span data-stu-id="8e940-106">Scope</span></span>|<span data-ttu-id="8e940-107">次要</span><span class="sxs-lookup"><span data-stu-id="8e940-107">Minor</span></span>|
|<span data-ttu-id="8e940-108">版本</span><span class="sxs-lookup"><span data-stu-id="8e940-108">Version</span></span>|<span data-ttu-id="8e940-109">4.5</span><span class="sxs-lookup"><span data-stu-id="8e940-109">4.5</span></span>|
|<span data-ttu-id="8e940-110">類型</span><span class="sxs-lookup"><span data-stu-id="8e940-110">Type</span></span>|<span data-ttu-id="8e940-111">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="8e940-111">Retargeting</span></span>|
|<span data-ttu-id="8e940-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8e940-112">Affected APIs</span></span>|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
