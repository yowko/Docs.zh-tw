---
ms.openlocfilehash: 0056baa1e5f0cdc5bfcf8b0e83c9490ec5722926
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235357"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a><span data-ttu-id="1ea2f-101">HttpUtility.JavaScriptStringEncode 會逸出 & 符號</span><span class="sxs-lookup"><span data-stu-id="1ea2f-101">HttpUtility.JavaScriptStringEncode escapes ampersand</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1ea2f-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1ea2f-102">Details</span></span>|<span data-ttu-id="1ea2f-103">從 .NET Framework 4.5 開始，<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> 會逸出 &amp; 字元。</span><span class="sxs-lookup"><span data-stu-id="1ea2f-103">Starting with the .NET Framework 4.5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=name> escapes the ampersand (&amp;) character.</span></span>|
|<span data-ttu-id="1ea2f-104">建議</span><span class="sxs-lookup"><span data-stu-id="1ea2f-104">Suggestion</span></span>|<span data-ttu-id="1ea2f-105">如果您的應用程式相依於此方法的舊版行為，您可以將 aspnet:JavaScriptDoNotEncodeAmpersand 設定新增至組態檔中的 [ASP.NET appSettings 項目](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="1ea2f-105">If your app depends on the previous behavior of this method, you can add an aspnet:JavaScriptDoNotEncodeAmpersand setting to the [ASP.NET appSettings element](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) in your configuration file.</span></span>|
|<span data-ttu-id="1ea2f-106">範圍</span><span class="sxs-lookup"><span data-stu-id="1ea2f-106">Scope</span></span>|<span data-ttu-id="1ea2f-107">次要</span><span class="sxs-lookup"><span data-stu-id="1ea2f-107">Minor</span></span>|
|<span data-ttu-id="1ea2f-108">版本</span><span class="sxs-lookup"><span data-stu-id="1ea2f-108">Version</span></span>|<span data-ttu-id="1ea2f-109">4.5</span><span class="sxs-lookup"><span data-stu-id="1ea2f-109">4.5</span></span>|
|<span data-ttu-id="1ea2f-110">類型</span><span class="sxs-lookup"><span data-stu-id="1ea2f-110">Type</span></span>|<span data-ttu-id="1ea2f-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="1ea2f-111">Runtime</span></span>|
|<span data-ttu-id="1ea2f-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1ea2f-112">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
