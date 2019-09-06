---
title: -errorreport (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253885"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="df8e6-102">-errorreport (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="df8e6-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="df8e6-103">此選項提供將 C# 編譯器內部錯誤回報給 Microsoft 的便利方式。</span><span class="sxs-lookup"><span data-stu-id="df8e6-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="df8e6-104">在 Windows Vista 和 Windows Server 2008 上，您為 Visual Studio 建立的錯誤報告設定不會覆寫透過 Windows 錯誤報告 (WER) 所做的設定。</span><span class="sxs-lookup"><span data-stu-id="df8e6-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="df8e6-105">WER 設定一律優先於 Visual Studio 錯誤報告設定。</span><span class="sxs-lookup"><span data-stu-id="df8e6-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="df8e6-106">語法</span><span class="sxs-lookup"><span data-stu-id="df8e6-106">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="df8e6-107">引數</span><span class="sxs-lookup"><span data-stu-id="df8e6-107">Arguments</span></span>
 <span data-ttu-id="df8e6-108">**none**</span><span class="sxs-lookup"><span data-stu-id="df8e6-108">**none**</span></span>  
 <span data-ttu-id="df8e6-109">將不會收集有關內部編譯器錯誤的報告，也不會將報告傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="df8e6-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="df8e6-110">**提示**提示您在收到內部編譯器錯誤時傳送報告。</span><span class="sxs-lookup"><span data-stu-id="df8e6-110">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="df8e6-111">**提示**是您在開發環境中編譯應用程式的預設值。</span><span class="sxs-lookup"><span data-stu-id="df8e6-111">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="df8e6-112">**佇列**將錯誤報表排入佇列。</span><span class="sxs-lookup"><span data-stu-id="df8e6-112">**queue** Queues the error report.</span></span> <span data-ttu-id="df8e6-113">當您使用系統管理認證登入時，您可以報告自上次登入後的任何失敗。</span><span class="sxs-lookup"><span data-stu-id="df8e6-113">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="df8e6-114">系統提示您傳送錯誤報告的頻率，最多三天一次。</span><span class="sxs-lookup"><span data-stu-id="df8e6-114">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="df8e6-115">**佇列**是您在命令列編譯應用程式的預設值。</span><span class="sxs-lookup"><span data-stu-id="df8e6-115">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="df8e6-116">**傳送**會自動將內部編譯器錯誤的報告傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="df8e6-116">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="df8e6-117">若要啟用此選項，您必須先同意 Microsoft 資料收集原則。</span><span class="sxs-lookup"><span data-stu-id="df8e6-117">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="df8e6-118">第一次在電腦上指定 **-errorreport:send** 時，編譯器訊息會請您參考包含 Microsoft 資料收集原則的網站。</span><span class="sxs-lookup"><span data-stu-id="df8e6-118">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="df8e6-119">備註</span><span class="sxs-lookup"><span data-stu-id="df8e6-119">Remarks</span></span>
 <span data-ttu-id="df8e6-120">編譯器無法處理原始程式碼檔案時，就會出現編譯器內部錯誤 (ICE)。</span><span class="sxs-lookup"><span data-stu-id="df8e6-120">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="df8e6-121">發生 ICE 時，編譯器不會產生輸出檔或任何有用的診斷，無法讓您修正程式碼。</span><span class="sxs-lookup"><span data-stu-id="df8e6-121">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="df8e6-122">在舊版中，當您收到 ICE 時，我們鼓勵您連絡 Microsoft 產品支援服務回報問題。</span><span class="sxs-lookup"><span data-stu-id="df8e6-122">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="df8e6-123">您可以使用 **-errorreport** 向 Visual C# 小組提供 ICE 資訊。</span><span class="sxs-lookup"><span data-stu-id="df8e6-123">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="df8e6-124">您的錯誤報告有助於改善未來的編譯器版本。</span><span class="sxs-lookup"><span data-stu-id="df8e6-124">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="df8e6-125">使用者能否傳送報告，取決於電腦和使用者原則權限。</span><span class="sxs-lookup"><span data-stu-id="df8e6-125">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="df8e6-126">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="df8e6-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="df8e6-127">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="df8e6-127">Open the project's **Properties** page.</span></span> <span data-ttu-id="df8e6-128">如需詳細資訊，請參閱[專案設計工具、建置頁 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="df8e6-128">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="df8e6-129">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="df8e6-129">Click the **Build** property page.</span></span>

3. <span data-ttu-id="df8e6-130">按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="df8e6-130">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="df8e6-131">修改**報告編譯器內部錯誤**屬性。</span><span class="sxs-lookup"><span data-stu-id="df8e6-131">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="df8e6-132">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>。</span><span class="sxs-lookup"><span data-stu-id="df8e6-132">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="df8e6-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df8e6-133">See also</span></span>

- [<span data-ttu-id="df8e6-134">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="df8e6-134">C# Compiler Options</span></span>](./index.md)
