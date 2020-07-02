---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614368"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a><span data-ttu-id="475d7-101">Resgen 拒絕從 web 載入內容</span><span class="sxs-lookup"><span data-stu-id="475d7-101">Resgen refuses to load content from the web</span></span>

#### <a name="details"></a><span data-ttu-id="475d7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="475d7-102">Details</span></span>

<span data-ttu-id="475d7-103">.resx 檔案可能包含二進位格式的輸入。</span><span class="sxs-lookup"><span data-stu-id="475d7-103">.resx files may contain binary formatted input.</span></span> <span data-ttu-id="475d7-104">如果您嘗試使用 resgen 來載入從不受信任位置下載的檔案，預設將無法載入輸入。</span><span class="sxs-lookup"><span data-stu-id="475d7-104">If you attempt to use resgen to load a file that was downloaded from an untrusted location, it will fail to load the input by default.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="475d7-105">建議</span><span class="sxs-lookup"><span data-stu-id="475d7-105">Suggestion</span></span>

<span data-ttu-id="475d7-106">需要從不受信任的位置載入二進位格式輸入的 Resgen 使用者，可以從輸入檔移除 web 標記，或套用退出怪癖。新增下列登錄設定，以套用全電腦的退出怪癖： [HKEY_LOCAL_MACHINE \software\microsoft.netframework\sdk] &quot; AllowProcessOfUntrustedResourceFiles &quot; = &quot; true&quot;</span><span class="sxs-lookup"><span data-stu-id="475d7-106">Resgen users who require loading binary formatted input from untrusted locations can either remove the mark of the web from the input file or apply the opt-out quirk.Add the following registry setting to apply the machine wide opt-out quirk: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span></span>

| <span data-ttu-id="475d7-107">名稱</span><span class="sxs-lookup"><span data-stu-id="475d7-107">Name</span></span>    | <span data-ttu-id="475d7-108">值</span><span class="sxs-lookup"><span data-stu-id="475d7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="475d7-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="475d7-109">Scope</span></span>   | <span data-ttu-id="475d7-110">Edge</span><span class="sxs-lookup"><span data-stu-id="475d7-110">Edge</span></span>        |
| <span data-ttu-id="475d7-111">版本</span><span class="sxs-lookup"><span data-stu-id="475d7-111">Version</span></span> | <span data-ttu-id="475d7-112">4.7.2</span><span class="sxs-lookup"><span data-stu-id="475d7-112">4.7.2</span></span>       |
| <span data-ttu-id="475d7-113">類型</span><span class="sxs-lookup"><span data-stu-id="475d7-113">Type</span></span>    | <span data-ttu-id="475d7-114">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="475d7-114">Retargeting</span></span> |
