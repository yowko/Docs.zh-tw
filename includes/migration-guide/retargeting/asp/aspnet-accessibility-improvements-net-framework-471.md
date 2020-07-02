---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614337"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a><span data-ttu-id="3007c-101">.NET Framework 4.7.1 中的 ASP.NET 協助工具改進功能</span><span class="sxs-lookup"><span data-stu-id="3007c-101">ASP.NET Accessibility Improvements in .NET Framework 4.7.1</span></span>

#### <a name="details"></a><span data-ttu-id="3007c-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3007c-102">Details</span></span>

<span data-ttu-id="3007c-103">從 .NET Framework 4.7.1 開始，ASP.NET 已經改善 ASP.NET Web 控制項如何搭配 Visual Studio 中的協助工具技術，來更妥善支援 ASP.NET 客戶。</span><span class="sxs-lookup"><span data-stu-id="3007c-103">Starting with the .NET Framework 4.7.1, ASP.NET has improved how ASP.NET Web Controls work with accessibility technology in Visual Studio to better support ASP.NET customers.</span></span>  <span data-ttu-id="3007c-104">這些包括下列變更：</span><span class="sxs-lookup"><span data-stu-id="3007c-104">These include the following changes:</span></span>

- <span data-ttu-id="3007c-105">在控制項中，實作遺漏 UI 協助工具模式的變更，例如在 [詳細資料檢視精靈] 的 [新增欄位] 對話方塊或 ListView 精靈的 [設定 ListView] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3007c-105">Changes to implement missing UI accessibility patterns in controls, like the Add Field dialog in the Details View wizard, or the Configure ListView dialog of the ListView wizard.</span></span>
- <span data-ttu-id="3007c-106">改善高對比模式顯示的變更，例如資料頁面巡覽區欄位編輯器。</span><span class="sxs-lookup"><span data-stu-id="3007c-106">Changes to improve the display in High Contrast mode, like the Data Pager Fields Editor.</span></span>
- <span data-ttu-id="3007c-107">改善控制項鍵盤瀏覽體驗的變更，例如 DataPager 控制項 [編輯頁面巡覽區欄位精靈] 的 [欄位] 對話方塊、[設定 ObjectContext] 對話方塊，或 [設定資料來源精靈] 的 [設定資料選取項目] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3007c-107">Changes to improve the keyboard navigation experiences for controls, like the Fields dialog in the Edit Pager Fields wizard of the DataPager control, the Configure ObjectContext dialog, or the Configure Data Selection dialog of the Configure Data Source wizard.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3007c-108">建議</span><span class="sxs-lookup"><span data-stu-id="3007c-108">Suggestion</span></span>

<span data-ttu-id="3007c-109">**如何選擇加入或退出這些變更**：為了讓 Visual Studio 設計工具可受益於這些變更，它必須在 .NET Framework 4.7.1 或更新版本上執行。</span><span class="sxs-lookup"><span data-stu-id="3007c-109">**How to opt in or out of these changes** In order for the Visual Studio Designer to benefit from these changes, it must run on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="3007c-110">Web 應用程式可以由下列任一種方式受益於這些變更：</span><span class="sxs-lookup"><span data-stu-id="3007c-110">The web application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="3007c-111">安裝 Visual Studio 2017 15.3 或更新版本中，依預設它會以下列 AppContext 參數支援新的協助工具功能。</span><span class="sxs-lookup"><span data-stu-id="3007c-111">Install Visual Studio 2017 15.3 or later, which supports the new accessibility features with the following AppContext Switch by default.</span></span>
- <span data-ttu-id="3007c-112">藉由將 `Switch.UseLegacyAccessibilityFeatures` AppContext 參數新增到 devenv.exe.config 檔案中的 `<runtime>` 區段，並將它設定為 `false`，選擇退出舊版協助工具行為，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3007c-112">Opt out of the legacy accessibility behaviors by adding the `Switch.UseLegacyAccessibilityFeatures` AppContext switch to the `<runtime>` section in the devenv.exe.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

<span data-ttu-id="3007c-113">以 .NET Framework 4.7.1 或更新版本為目標，並且想要保留舊版協助工具行為的應用程式，可以藉由明確將此 AppContext 參數設為 `true`，選擇加入舊版的協助工具功能。</span><span class="sxs-lookup"><span data-stu-id="3007c-113">Applications that target the .NET Framework 4.7.1 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="3007c-114">名稱</span><span class="sxs-lookup"><span data-stu-id="3007c-114">Name</span></span>    | <span data-ttu-id="3007c-115">值</span><span class="sxs-lookup"><span data-stu-id="3007c-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3007c-116">影響範圍</span><span class="sxs-lookup"><span data-stu-id="3007c-116">Scope</span></span>   | <span data-ttu-id="3007c-117">Minor</span><span class="sxs-lookup"><span data-stu-id="3007c-117">Minor</span></span>       |
| <span data-ttu-id="3007c-118">版本</span><span class="sxs-lookup"><span data-stu-id="3007c-118">Version</span></span> | <span data-ttu-id="3007c-119">4.7.1</span><span class="sxs-lookup"><span data-stu-id="3007c-119">4.7.1</span></span>       |
| <span data-ttu-id="3007c-120">類型</span><span class="sxs-lookup"><span data-stu-id="3007c-120">Type</span></span>    | <span data-ttu-id="3007c-121">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="3007c-121">Retargeting</span></span> |
