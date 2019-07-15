---
ms.openlocfilehash: 9d09f598538b9d5ee3f995d6281b8eb4b2668050
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802507"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a><span data-ttu-id="828e7-101">WPF 拼字檢查功能所擲回的 ObjectDisposedException</span><span class="sxs-lookup"><span data-stu-id="828e7-101">ObjectDisposedException thrown by WPF spellchecker</span></span>

|   |   |
|---|---|
|<span data-ttu-id="828e7-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="828e7-102">Details</span></span>|<span data-ttu-id="828e7-103">在應用程式關閉期間，WPF 應用程式偶爾會因拼字檢查功能所擲回的 <xref:System.ObjectDisposedException?displayProperty=name> 而損毀。</span><span class="sxs-lookup"><span data-stu-id="828e7-103">WPF applications occasionally crash during application shutdown with an <xref:System.ObjectDisposedException?displayProperty=name> thrown by the spellchecker.</span></span> <span data-ttu-id="828e7-104">此問題已在 .NET Framework 4.7 WPF 中透過依正常程序處理例外狀況來修正，進而確保應用程式不會再受到負面影響。</span><span class="sxs-lookup"><span data-stu-id="828e7-104">This is fixed in .NET Framework 4.7 WPF by handling the exception gracefully, and thus ensuring that applications are no longer adversely affected.</span></span> <span data-ttu-id="828e7-105">請注意，在偵錯工具下執行的應用程式偶爾還是會發生第一個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="828e7-105">It should be noted that occasional first-chance exceptions would continue to be observed in applications running under a debugger.</span></span>|
|<span data-ttu-id="828e7-106">建議</span><span class="sxs-lookup"><span data-stu-id="828e7-106">Suggestion</span></span>|<span data-ttu-id="828e7-107">升級至 .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="828e7-107">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="828e7-108">範圍</span><span class="sxs-lookup"><span data-stu-id="828e7-108">Scope</span></span>|<span data-ttu-id="828e7-109">Edge</span><span class="sxs-lookup"><span data-stu-id="828e7-109">Edge</span></span>|
|<span data-ttu-id="828e7-110">版本</span><span class="sxs-lookup"><span data-stu-id="828e7-110">Version</span></span>|<span data-ttu-id="828e7-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="828e7-111">4.6.1</span></span>|
|<span data-ttu-id="828e7-112">類型</span><span class="sxs-lookup"><span data-stu-id="828e7-112">Type</span></span>|<span data-ttu-id="828e7-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="828e7-113">Runtime</span></span>|

