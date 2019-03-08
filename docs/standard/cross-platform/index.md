---
title: 使用 .NET Framework 進行多平台開發
ms.date: 07/18/2018
ms.technology: dotnet-standard
ms.assetid: b153baaa-130c-4169-860b-e580591de91e
author: mairaw
ms.author: mairaw
---
# <a name="developing-for-multiple-platforms-with-the-net-framework"></a>使用 .NET Framework 進行多平台開發

您可以使用 .NET Framework 和 Visual Studio，針對 Microsoft 和非 Microsoft 平台來開發應用程式。
  
## <a name="options-for-cross-platform-development"></a>跨平台開發的選項

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]
  
 若要針對多重平台進行開發，您可以共用原始程式碼或二進位檔，並且可以在 .NET Framework 程式碼與 Windows 執行階段 API 之間進行呼叫。  
  
|如果您想要...|請使用...|  
|-----------------------|------------|  
|在 Windows Phone 8.1 與 Windows 8.1 應用程式之間共用原始程式碼|**共用專案**（在 Visual Studio 2013 Update 2 的通用應用程式範本）。<br /><br /> -目前沒有 Visual Basic 支援。<br />-您可以使用 # 不同平台特定程式碼`if`陳述式。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   [開始撰寫程式碼](/windows/uwp/get-started/create-uwp-apps)<br />-   [使用 Visual Studio 來建置通用 XAML 應用程式](https://devblogs.microsoft.com/visualstudio/using-visual-studio-to-build-universal-xaml-apps/)（部落格文章）<br />-   [使用 Visual Studio 來建立 XAML 交集應用程式](https://channel9.msdn.com/Events/Build/2014/3-591)（影片）|  
|在目標為不同平台的應用程式之間共用二進位檔|**可攜式類別庫專案**是跨平台的程式碼。<br /><br /> -這種方法通常用於實作商務邏輯的程式碼。<br />-您可以使用 Visual Basic 或 C#。<br />API 支援會因平台而異。<br />-Windows 8.1 和 Windows Phone 8.1 為目標的可攜式類別庫專案支援 Windows 執行階段 Api 和 XAML。 舊版可攜式類別程式庫中沒有提供這些功能。<br />-如有需要您可以使用介面或抽象類別來擷取出平台特定程式碼。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   [可攜式類別庫](cross-platform-development-with-the-portable-class-library.md)<br />-   [您如何讓可攜式類別程式庫工作](https://blogs.msdn.microsoft.com/dsplaisted/2012/08/27/how-to-make-portable-class-libraries-work-for-you/)（部落格文章）<br />-   [搭配 MVVM 使用可攜式類別庫](using-portable-class-library-with-model-view-view-model.md) <br />-   [多個平台為目標的程式庫的應用程式資源](app-resources-for-libraries-that-target-multiple-platforms.md) <br />-   [.NET portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) （Visual Studio 擴充功能）|  
|針對非 Windows 8.1 和 Windows Phone 8.1 的平台共用原始程式碼|**加入做為連結**功能。<br /><br /> -這種方法適合是通用於這兩個應用程式，但可攜性，因為某些原因的應用程式邏輯。 您可以將此功能用於 C# 或 Visual Basic 程式碼。<br />     例如，Windows Phone 8 和 Windows 8 共用 Windows 執行階段 API，但可攜式類別庫不支援那些平台的 Windows 執行階段。 您可以使用 `Add as link`，在 Windows Phone 8 應用程式與目標為 Windows 8 的 Windows 市集應用程式之間，共用一般 Windows 執行階段程式碼。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   [加入做為連結使用的共用程式碼](https://docs.microsoft.com/previous-versions/windows/apps/jj714082(v=vs.105))<br />-   [如何：將現有的項目加入至專案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))|  
|使用 .NET Framework 或從 .NET Framework 程式碼呼叫 Windows 執行階段 API，以撰寫 Windows 市集應用程式|**Windows 執行階段 Api**從您的.NET Framework C# 或 Visual Basic 程式碼，並使用.NET Framework 建立 Windows 市集應用程式。 請注意這兩個平台之間的 API 差異。 不過，有類別可以幫助您處理這些差異。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   [Windows 市集應用程式和 Windows 執行階段的.NET framework 支援](support-for-windows-store-apps-and-windows-runtime.md) <br />-   [傳遞 URI 給 Windows 執行階段](passing-a-uri-to-the-windows-runtime.md) <br />-   <xref:System.IO.WindowsRuntimeStreamExtensions><br />-    <xref:System.WindowsRuntimeSystemExtensions>|  
|針對非 Microsoft 平台建立 .NET Framework 應用程式|**可攜式類別庫參考組件**在.NET Framework 和 Visual Studio 延伸模組或協力廠商工具，例如 Xamarin。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   [可攜式類別程式庫現在可在所有平台上。](https://devblogs.microsoft.com/dotnet/portable-class-library-pcl-now-available-on-all-platforms/) (部落格文章)<br />-   [Xamarin 文件](/xamarin)|  
|使用 JavaScript 和 HTML 進行跨平台開發|**通用應用程式範本**在 Visual Studio 2013 中，更新 2，以針對 Windows 8.1 和 Windows Phone 8.1 開發 Windows 執行階段 Api。 目前，您無法使用 JavaScript 和 HTML 搭配 .NET Framework API 來開發跨平台應用程式。<br /><br /> 如需詳細資訊，請參閱：<br /><br /> -   [JavaScript 專案範本](https://docs.microsoft.com/previous-versions/windows/apps/hh758331%28v=win.10%29)<br />-   [使用 Windows Phone 的 JavaScript 將 Windows 執行階段應用程式移植](https://docs.microsoft.com/previous-versions/windows/apps/dn636144%28v=win.10%29)|