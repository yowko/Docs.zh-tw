---
ms.openlocfilehash: 8049bf01bc10c5913fa11b25e49afd1b1317eecc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802948"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a><span data-ttu-id="6d73c-101">WPF 拼字檢查以非預期的方式失敗</span><span class="sxs-lookup"><span data-stu-id="6d73c-101">WPF Spell Checking fails in unexpected ways</span></span>

|   |   |
|---|---|
|<span data-ttu-id="6d73c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6d73c-102">Details</span></span>|<span data-ttu-id="6d73c-103">這包括一些 WPF 拼字檢查工具問題：</span><span class="sxs-lookup"><span data-stu-id="6d73c-103">This includes a number of WPF Spell Checker issues:</span></span><ul><li><span data-ttu-id="6d73c-104">WPF 拼字檢查工具有時會擲回 <xref:System.Runtime.InteropServices.COMException?displayProperty=name></span><span class="sxs-lookup"><span data-stu-id="6d73c-104">WPF Spell Checker sometimes throws <xref:System.Runtime.InteropServices.COMException?displayProperty=name></span></span></li><li><span data-ttu-id="6d73c-105">使用 [以不同的使用者身分執行] 來啟動應用程式時，WPF 拼字檢查工具會失敗並顯示 <xref:System.UnauthorizedAccessException></span><span class="sxs-lookup"><span data-stu-id="6d73c-105">WPF Spell Checker fails with <xref:System.UnauthorizedAccessException> when applications are launched using 'run as different user'</span></span></li><li><span data-ttu-id="6d73c-106">WPF 拼字檢查工具會誤將複合字識別為拼字錯誤，例如德文中的 'Hausnummer'。</span><span class="sxs-lookup"><span data-stu-id="6d73c-106">WPF Spell Checker incorrectly identifies spelling errors in compound words like 'Hausnummer' in German.</span></span></li></ul>|
|<span data-ttu-id="6d73c-107">建議</span><span class="sxs-lookup"><span data-stu-id="6d73c-107">Suggestion</span></span>|<span data-ttu-id="6d73c-108">問題 #1 - 此問題已在 .NET Framework 4.6.2 中修正。問題 #2 - 使用 [以不同的使用者身分執行] 來啟動應用程式時，不再支援 WPF 拼字檢查工具。</span><span class="sxs-lookup"><span data-stu-id="6d73c-108">Issue #1 - This has been fixed in .NET Framework 4.6.2 Issue #2 - WPF Spell Checker is no longer supported when applications are launched using 'run as different user'.</span></span> <span data-ttu-id="6d73c-109">從 .NET Framework 4.6.2 開始，以這種方式啟動的應用程式將不會再意外損毀 - 而是以無訊息的方式停用拼字檢查工具。</span><span class="sxs-lookup"><span data-stu-id="6d73c-109">Starting .NET Framework 4.6.2, applications launched in this manner will no longer crash unexpectedly - instead the Spell Checker will be silently disabled.</span></span> <span data-ttu-id="6d73c-110">問題 #3 - 此問題已在 .NET Framework 4.6.2 中修正。</span><span class="sxs-lookup"><span data-stu-id="6d73c-110">Issue #3 - This has been fixed in .NET Framework 4.6.2.</span></span>|
|<span data-ttu-id="6d73c-111">範圍</span><span class="sxs-lookup"><span data-stu-id="6d73c-111">Scope</span></span>|<span data-ttu-id="6d73c-112">Edge</span><span class="sxs-lookup"><span data-stu-id="6d73c-112">Edge</span></span>|
|<span data-ttu-id="6d73c-113">版本</span><span class="sxs-lookup"><span data-stu-id="6d73c-113">Version</span></span>|<span data-ttu-id="6d73c-114">4.6.1</span><span class="sxs-lookup"><span data-stu-id="6d73c-114">4.6.1</span></span>|
|<span data-ttu-id="6d73c-115">類型</span><span class="sxs-lookup"><span data-stu-id="6d73c-115">Type</span></span>|<span data-ttu-id="6d73c-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="6d73c-116">Runtime</span></span>|

