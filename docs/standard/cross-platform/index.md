---
title: 使用 .NET Framework 進行多平台開發
ms.date: 07/18/2018
ms.technology: dotnet-standard
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf5c48640b56b5515cc8240ef12319515b859f83
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938024"
---
# <a name="developing-for-multiple-platforms-with-the-net-framework"></a>使用 .NET Framework 進行多平台開發

您可以使用 .NET Framework 和 Visual Studio，針對 Microsoft 和非 Microsoft 平台來開發應用程式。
  
## <a name="options-for-cross-platform-development"></a>跨平台開發的選項

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]
  
 若要針對多重平台進行開發，您可以共用原始程式碼或二進位檔，並且可以在 .NET Framework 程式碼與 Windows 執行階段 API 之間進行呼叫。  
  
|如果您想要...|請使用...|  
|-----------------------|------------|  
|在 Windows Phone 8.1 與 Windows 8.1 應用程式之間共用原始程式碼|**共用專案**（Visual Studio 2013 中的通用應用程式範本，Update 2）。<br /><br /> -目前不支援 Visual Basic。<br />-您可以使用 #`if` 語句來分隔平臺特定程式碼。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   [開始](/windows/uwp/get-started/create-uwp-apps)撰寫程式碼<br />-   [使用 Visual Studio 來建立通用 XAML 應用程式](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/)（blog 文章）<br />[使用 Visual Studio 建立 XAML 聚合式應用程式](https://channel9.msdn.com/Events/Build/2014/3-591)-   （影片）|  
|在目標為不同平台的應用程式之間共用二進位檔|**可移植的類別庫專案**，適用于與平臺無關的程式碼。<br /><br /> -這種方法通常用於執行商務邏輯的程式碼。<br />-您可以使用 Visual Basic 或C#。<br />-API 支援會因平臺而異。<br />-以 Windows 8.1 和 Windows Phone 8.1 為目標的可移植類別庫專案支援 Windows 執行階段 Api 和 XAML。 舊版可攜式類別程式庫中沒有提供這些功能。<br />-如有需要，您可以使用介面或抽象類別來抽象化平臺特定程式碼。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   的[可移植類別庫](cross-platform-development-with-the-portable-class-library.md)<br />-   [如何讓可移植的類別庫適用于您](https://docs.microsoft.com/archive/blogs/dsplaisted/how-to-make-portable-class-libraries-work-for-you)（blog 文章）<br />搭配[MVVM 使用可移植類別庫的](using-portable-class-library-with-model-view-view-model.md)-    <br />[針對以多個平臺為目標的程式庫 -   應用程式資源](app-resources-for-libraries-that-target-multiple-platforms.md) <br />-   [.net 可攜性分析器](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)（Visual Studio 延伸模組）|  
|針對非 Windows 8.1 和 Windows Phone 8.1 的平台共用原始程式碼|**新增為連結**功能。<br /><br /> -這個方法適用于這兩個應用程式通用的應用程式邏輯，但基於某些原因而無法移植。 您可以將此功能用於 C# 或 Visual Basic 程式碼。<br />     例如，Windows Phone 8 和 Windows 8 共用 Windows 執行階段 API，但可攜式類別庫不支援那些平台的 Windows 執行階段。 您可以使用 `Add as link`，在 Windows Phone 8 應用程式與目標為 Windows 8 的 Windows 市集應用程式之間，共用一般 Windows 執行階段程式碼。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   [共用程式碼與新增為連結](https://docs.microsoft.com/previous-versions/windows/apps/jj714082(v=vs.105))<br />-   [如何：將現有的專案加入至專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))|  
|使用 .NET Framework 或從 .NET Framework 程式碼呼叫 Windows 執行階段 API，以撰寫 Windows 市集應用程式|從您的 .NET Framework C#或 Visual Basic 程式碼**Windows 執行階段 api** ，並使用 .NET Framework 來建立 Windows Store 應用程式。 請注意這兩個平台之間的 API 差異。 不過，有類別可以幫助您處理這些差異。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> [適用于 Windows Store 應用程式和 Windows 執行階段的 -   .NET Framework 支援](support-for-windows-store-apps-and-windows-runtime.md) <br />-   將[URI 傳遞至 Windows 執行階段](passing-a-uri-to-the-windows-runtime.md) <br />-   <xref:System.IO.WindowsRuntimeStreamExtensions><br />-    <xref:System.WindowsRuntimeSystemExtensions>|  
|針對非 Microsoft 平台建立 .NET Framework 應用程式|.NET Framework 中的**可移植類別庫參考元件**，以及 Visual Studio 延伸模組或協力廠商工具（例如 Xamarin）。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> [所有平臺上現在都可使用 -   的可移植類別庫。](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/) (部落格文章)<br />-   [Xamarin 檔](/xamarin)|  
|使用 JavaScript 和 HTML 進行跨平台開發|Visual Studio 2013、Update 2 中的**通用應用程式範本**，可針對 Windows 8.1 和 Windows Phone 8.1 的 Windows 執行階段 api 進行開發。 目前，您無法使用 JavaScript 和 HTML 搭配 .NET Framework API 來開發跨平台應用程式。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   [JavaScript 專案範本](https://docs.microsoft.com/previous-versions/windows/apps/hh758331%28v=win.10%29)<br />-   [使用 JavaScript 將 Windows 執行階段應用程式移植至 Windows Phone](https://docs.microsoft.com/previous-versions/windows/apps/dn636144%28v=win.10%29)|
