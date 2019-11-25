---
title: 擴充 Visual Basic 應用程式模型
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic Application Model, extending
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
ms.openlocfilehash: 46c18ab540c90c4147514685c2acc824755b435f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976854"
---
# <a name="extending-the-visual-basic-application-model"></a>擴充 Visual Basic 應用程式模型

您可以藉由覆寫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 類別的 `Overridable` 成員，將功能新增至應用程式模型。 這項技術可讓您自訂應用程式模型的行為，並在應用程式啟動和關閉時，將呼叫新增至您自己的方法。

## <a name="visual-overview-of-the-application-model"></a>應用程式模型的視覺化總覽

本節會以視覺化方式呈現 Visual Basic 應用程式模型中的函式呼叫順序。 下一節將詳細說明每個函數的用途。

下圖顯示一般 Visual Basic Windows Forms 應用程式中的應用程式模型呼叫順序。 序列會在 `Sub Main` 程式呼叫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> 方法時啟動。

![顯示應用程式模型呼叫順序的圖表。](./media/extending-the-visual-basic-application-model/application-model-call-sequence.gif)

Visual Basic 應用程式模型也會提供 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> 和 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> 事件。 下列圖形顯示引發這些事件的機制。

![顯示引發 StartupNextInstance 事件之 OnStartupNextInstance 方法的圖表。](./media/extending-the-visual-basic-application-model/raise-startupnextinstance-event.gif)

![顯示引發 UnhandledException 事件之6Bb2d5d6-f49a-4c6d-a988-478afb86dbe9 方法的圖表。](./media/extending-the-visual-basic-application-model/raise-unhandledexception-event.gif)

## <a name="overriding-the-base-methods"></a>覆寫基底方法

<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> 方法會定義 `Application` 方法的執行順序。 根據預設，Windows Forms 應用程式的 `Sub Main` 程式會呼叫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> 方法。

如果應用程式是一般應用程式（多重實例應用程式）或單一實例應用程式的第一個實例，則 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> 方法會依下列循序執行 `Overridable` 方法：

1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> 根據預設，這個方法會設定主應用程式執行緒的視覺化樣式、文字顯示樣式和目前主體（如果應用程式使用 Windows 驗證），而且如果 `/nosplash` 或 `-nosplash` 都不是用來做為命令列引數，則會呼叫 `ShowSplashScreen`。

     如果此函數傳回 `False`，則會取消應用程式啟動順序。 當應用程式不應該執行的情況下，這會很有用。

     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> 方法會呼叫下列方法：

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> 決定應用程式是否已定義啟動顯示畫面，如果有，則會在個別的執行緒上顯示啟動顯示畫面。

         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> 方法包含的程式碼，會在至少顯示 [<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>] 屬性所指定之毫秒數的啟動顯示畫面。 若要使用這項功能，您必須使用 [**專案設計**工具] （將 [`My.Application.MinimumSplashScreenDisplayTime`] 屬性設為兩秒），將啟動顯示畫面新增至應用程式，或在覆寫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> 或 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> 方法的方法中設定 `My.Application.MinimumSplashScreenDisplayTime` 屬性。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>。

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> 允許設計工具發出初始化啟動顯示畫面的程式碼。

         根據預設，這個方法不會執行任何操作。 如果您在 [Visual Basic**專案設計**工具] 中選取應用程式的啟動顯示畫面，則設計工具會以將 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> 屬性設定為啟動顯示畫面表單新實例的方法，覆寫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> 方法。

2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A> 提供用來引發 `Startup` 事件的擴充點。 如果此函數傳回 `False`，應用程式啟動順序就會停止。

     根據預設，這個方法會引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> 事件。 如果事件處理常式將事件引數的 <xref:System.ComponentModel.CancelEventArgs.Cancel> 屬性設定為 `True`，則方法會傳回 `False` 以取消應用程式啟動。

3. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A> 提供在初始化完成之後，主應用程式已準備好開始執行的起始點。

     根據預設，在進入 Windows Forms 訊息迴圈之前，這個方法會呼叫 `OnCreateMainForm` （以建立應用程式的主要表單）和 `HideSplashScreen` （以關閉啟動顯示畫面）方法：

    1. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> 提供一種方法，讓設計工具發出初始化主要表單的程式碼。

         根據預設，這個方法不會執行任何操作。 不過，當您在 [Visual Basic**專案設計**工具] 中選取應用程式的主要表單時，設計工具會使用將 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> 屬性設定為主要表單新實例的方法來覆寫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> 方法。

    2. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A> 如果應用程式已定義啟動顯示畫面，而且已開啟，則此方法會關閉啟動顯示畫面。

         根據預設，這個方法會關閉啟動顯示畫面。

4. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> 提供一種方法，可自訂應用程式的另一個實例啟動時，單一實例應用程式的行為方式。

     根據預設，這個方法會引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> 事件。

5. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A> 提供用來引發 `Shutdown` 事件的擴充點。 如果主應用程式中發生未處理的例外狀況，則不會執行此方法。

     根據預設，這個方法會引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> 事件。

6. <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A> 如果未處理的例外狀況發生在上述任何一種方法中，就會執行。

     根據預設，只要未附加偵錯工具，而且應用程式正在處理 `UnhandledException` 事件，這個方法就會引發 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> 事件。

 如果應用程式是單一實例應用程式，且應用程式已在執行中，則應用程式的後續實例會在應用程式的原始實例上呼叫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> 方法，然後結束。

 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance(Microsoft.VisualBasic.ApplicationServices.StartupNextInstanceEventArgs)> 的函式會呼叫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> 屬性，以決定要用於應用程式表單的文字轉譯引擎。 根據預設，<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> 屬性會傳回 `False`，表示使用的是 GDI 文字轉譯引擎，這是 Visual Basic 2005 和更新版本中的預設值。 您可以覆寫 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> 屬性以傳回 `True`，這表示會使用 GDI + 文字轉譯引擎，這是 Visual Basic .NET 2002 和 Visual Basic .NET 2003 中的預設值。

## <a name="configuring-the-application"></a>設定應用程式

 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> 類別是 Visual Basic 應用程式模型的一部分，提供設定應用程式的受保護屬性。 這些屬性應設定于實作為執行類別的函式中。

 在預設的 Windows Forms 專案中，[**專案設計**工具] 會建立程式碼，以使用設計工具設定來設定屬性。 只有在應用程式啟動時，才會使用這些屬性;在應用程式啟動後設定它們不會有任何作用。

|屬性|4|在 [專案設計工具] 的 [應用程式] 窗格中設定|
|---|---|---|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|應用程式是以單一實例或多重實例應用程式的方式執行。|**設為單一實例應用程式**核取方塊|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|如果應用程式將使用符合 Windows XP 的視覺化樣式。|**啟用 XP 視覺化樣式**核取方塊|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|如果應用程式會在應用程式結束時自動儲存應用程式的使用者設定變更。|[**關閉時儲存我的設定**] 核取方塊|
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|造成應用程式終止的原因，例如啟動表單關閉時，或最後一個表單關閉時。|**關機模式**清單|

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>
- [Visual Basic 應用程式模型概觀](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
- [專案設計工具、應用程式頁面 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
