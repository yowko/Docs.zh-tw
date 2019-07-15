---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802479"
---
### <a name="wpf-printing-stack-update"></a><span data-ttu-id="a117a-101">WPF 列印堆疊更新</span><span class="sxs-lookup"><span data-stu-id="a117a-101">WPF Printing Stack Update</span></span>

|   |   |
|---|---|
|<span data-ttu-id="a117a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a117a-102">Details</span></span>|<span data-ttu-id="a117a-103">使用 <xref:System.Printing.PrintQueue?displayProperty=name> 的 WPF 列印 API 現在會呼叫 Windows 的列印文件套件 API，以支援目前已淘汰的 XPS 列印 API。</span><span class="sxs-lookup"><span data-stu-id="a117a-103">WPF's Printing APIs using <xref:System.Printing.PrintQueue?displayProperty=name> now call Window's Print Document Package API in favor of the now deprecated XPS Print API.</span></span> <span data-ttu-id="a117a-104">進行這項變更是考慮到服務能力；使用者和開發人員都不應該會看到行為或 API 使用方式中有任何變更。</span><span class="sxs-lookup"><span data-stu-id="a117a-104">The change was made with serviceability in mind; neither users nor developers should see any changes in behavior or API usage.</span></span> <span data-ttu-id="a117a-105">在 Windows 10 Creators Update 中執行時，預設會啟用新的列印堆疊。</span><span class="sxs-lookup"><span data-stu-id="a117a-105">The new printing stack is enabled by default when running in Windows 10 Creators Update.</span></span> <span data-ttu-id="a117a-106">舊版 Windows 上的舊列印堆疊仍會繼續如往常一般運作。</span><span class="sxs-lookup"><span data-stu-id="a117a-106">The old printing stack will still continue to work just as before in older Windows versions.</span></span>|
|<span data-ttu-id="a117a-107">建議</span><span class="sxs-lookup"><span data-stu-id="a117a-107">Suggestion</span></span>|<span data-ttu-id="a117a-108">若要在 Windows 10 Creators Update 中使用舊堆疊，請將 <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> 登錄機碼的 <code>UseXpsOMPrinting</code> REG_DWORD 值設為 <code>1</code>。</span><span class="sxs-lookup"><span data-stu-id="a117a-108">To use the old stack in Windows 10 Creators Update, set the <code>UseXpsOMPrinting</code> REG_DWORD value of the <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> registry key to <code>1</code>.</span></span>|
|<span data-ttu-id="a117a-109">範圍</span><span class="sxs-lookup"><span data-stu-id="a117a-109">Scope</span></span>|<span data-ttu-id="a117a-110">Edge</span><span class="sxs-lookup"><span data-stu-id="a117a-110">Edge</span></span>|
|<span data-ttu-id="a117a-111">版本</span><span class="sxs-lookup"><span data-stu-id="a117a-111">Version</span></span>|<span data-ttu-id="a117a-112">4.7</span><span class="sxs-lookup"><span data-stu-id="a117a-112">4.7</span></span>|
|<span data-ttu-id="a117a-113">類型</span><span class="sxs-lookup"><span data-stu-id="a117a-113">Type</span></span>|<span data-ttu-id="a117a-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="a117a-114">Runtime</span></span>|

