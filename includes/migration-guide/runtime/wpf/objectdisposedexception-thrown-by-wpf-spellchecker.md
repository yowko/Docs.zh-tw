---
ms.openlocfilehash: b836b26f3f52e9d0cc78feb764629bd2fa306657
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621779"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="8fb59-101">WPF 拼字檢查功能所擲回的 ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="8fb59-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

#### <a name="details"></a><span data-ttu-id="8fb59-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8fb59-102">Details</span></span>

<span data-ttu-id="8fb59-103">在應用程式關閉期間，WPF 應用程式偶爾會因拼字檢查功能所擲回的 <xref:System.ObjectDisposedException?displayProperty=fullName> 而損毀。</span><span class="sxs-lookup"><span data-stu-id="8fb59-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=fullName> thrown by the spellchecker.</span></span> <span data-ttu-id="8fb59-104">此問題已在 .NET Framework 4.7 WPF 中透過依正常程序處理例外狀況來修正，進而確保應用程式不會再受到負面影響。</span><span class="sxs-lookup"><span data-stu-id="8fb59-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="8fb59-105">請注意，在偵錯工具下執行的應用程式偶爾還是會發生第一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8fb59-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8fb59-106">建議</span><span class="sxs-lookup"><span data-stu-id="8fb59-106">Suggestion</span></span>

<span data-ttu-id="8fb59-107">升級至 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="8fb59-107">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="8fb59-108">名稱</span><span class="sxs-lookup"><span data-stu-id="8fb59-108">Name</span></span>    | <span data-ttu-id="8fb59-109">值</span><span class="sxs-lookup"><span data-stu-id="8fb59-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8fb59-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="8fb59-110">Scope</span></span>   |<span data-ttu-id="8fb59-111">Edge</span><span class="sxs-lookup"><span data-stu-id="8fb59-111">Edge</span></span>|
|<span data-ttu-id="8fb59-112">版本</span><span class="sxs-lookup"><span data-stu-id="8fb59-112">Version</span></span>|<span data-ttu-id="8fb59-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="8fb59-113">4.6.1</span></span>|
|<span data-ttu-id="8fb59-114">類型</span><span class="sxs-lookup"><span data-stu-id="8fb59-114">Type</span></span>|<span data-ttu-id="8fb59-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="8fb59-115">Runtime</span></span>|
