---
title: HOW TO：偵錯 Windows 服務應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
ms.openlocfilehash: 02ea82bf224349e6ea7a5afbfb3c38ba50df46f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720362"
---
# <a name="how-to-debug-windows-service-applications"></a>HOW TO：偵錯 Windows 服務應用程式
服務必須從服務控制管理員內容之中執行，而不是從 Visual Studio 之中執行。 因此，對服務進行偵錯不像是對其他 Visual Studio 應用程式類型進行偵錯那樣簡單直接。 若要對服務進行偵錯，您必須啟動服務，然後將偵錯工具附加至執行中的處理序。 之後就可以使用 Visual Studio 所有的標準偵錯功能，對應用程式進行偵錯。  
  
> [!CAUTION]
>  除非您知道處理序的內容，並了解附加至處理序以及可能會刪除該處理序的後果，否則就不應該附加至處理序。 例如，如果您附加至 WinLogon 處理序，再停止偵錯，系統將會中止，因為系統沒有 WinLogon 就無法運作。  
  
 您只可以將偵錯工具附加至執行中的服務。 附加程序會中斷服務的目前運作，但不會實際停止或暫停服務的處理。 也就是說，當您開始偵錯時，如果您的服務正在執行，技術上來說，正在進行偵錯的服務還是處於啟動狀態，但已暫停其處理。  
  
 附加至處理序之後，您可以設定中斷點，並使用這些中斷點對程式碼進行偵錯。 一旦您結束用來附加至處理序的對話方塊，就會立即處於偵錯模式中。 您可以使用服務控制管理員來啟動、停止、暫停及繼續服務，以此方式來叫用您所設定的中斷點。 偵錯成功之後，您就可以移除這項虛擬服務。  
  
 本文涵蓋對本機電腦上執行的服務進行偵錯，但您也可以對遠端電腦上執行的 Windows 服務進行偵錯。 請參閱[遠端偵錯](/visualstudio/debugger/debug-installed-app-package)。  
  
> [!NOTE]
>  對 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法進行偵錯可能是項困難的工作，因為服務控制管理員對於啟動服務的所有嘗試都強加上 30 秒的限制。 如需詳細資訊，請參閱[疑難排解：對 Windows 服務進行偵錯](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)。  
  
> [!WARNING]
>  若要取得有關偵錯的有意義資訊，Visual Studio 偵錯工具必須在符號檔中找到正在進行偵錯的二進位檔案。 如果您想要對建置於 Visual Studio 中的服務進行偵錯，符號檔 (.pdb 檔) 會與可執行檔或程式庫位於同一個資料夾中，並且偵錯工具會自動載入檔案。 如果您想要對非您所建置的服務進行偵錯，則應該先找到服務的符號，並確定偵錯工具可以找到這些符號。 請參閱[指定符號 (.pdb) 和原始程式檔](https://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b)。 如果您想要對系統處理序進行偵錯，或想要在您的服務中有系統呼叫的符號，則應該加入 Microsoft 符號伺服器。 請參閱[偵錯符號](/windows/desktop/DxTechArts/debugging-with-symbols) \(英文\)。  
  
### <a name="to-debug-a-service"></a>偵錯服務  
  
1.  在偵錯組態中建置您的服務。  
  
2.  安裝您的服務。 如需詳細資訊，請參閱[＜How to：安裝和解除安裝服務](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)。  
  
3.  從 [服務控制管理員]、[伺服器總管] 或從程式碼啟動您的服務。 如需詳細資訊，請參閱[＜How to：啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)。  
  
4.  使用系統管理認證啟動 Visual Studio，以便能夠附加至系統處理程序。  
  
5.  (選擇性) 在 Visual Studio 功能表列上，選擇 [工具]、[選項]。 在 [選項] 對話方塊中，選擇 [偵錯]、[符號]，選取 [Microsoft 符號伺服器] 核取方塊，然後選擇 [確定] 按鈕。  
  
6.  在功能表列上，從 [偵錯] 或 [工具] 功能表中選擇 [附加至處理序]。 (鍵盤：Ctrl+Alt+P)  
  
     [處理序] 對話方塊隨即出現。  
  
7.  選取 [顯示所有使用者的處理序] 核取方塊。  
  
8.  在 [可使用的處理序] 區段中，選擇服務的處理序，然後選擇 [附加]。  
  
    > [!TIP]
    >  處理序的名稱和您的服務可執行檔名稱相同。  
  
     [附加至處理序]  對話方塊隨即出現。  
  
9. 選擇適當選項，然後選擇 [確定] 關閉對話方塊。  
  
    > [!NOTE]
    >  您現在已處於偵錯模式中。  
  
10. 在程式碼中設定任何想要使用的中斷點。  
  
11. 存取服務控制管理員並操作您的服務，傳送停止、暫停和繼續命令來叫用中斷點。 如需執行服務控制管理員的詳細資訊，請參閱[如何：啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)。 另請參閱[疑難排解：對 Windows 服務進行偵錯](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)。  
  
## <a name="debugging-tips-for-windows-services"></a>Windows 服務的偵錯秘訣  
 附加至服務的處理序可讓您對大多數的服務程式碼進行偵錯，但並非所有的服務程式碼都可用這種方式偵錯。 例如，由於已經啟動服務，因此您無法以這種方式對服務之 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中的程式碼，或對用來載入服務之 `Main` 方法中的程式碼進行偵錯。 解決這個限制的其中一個方法，是在您的服務應用程式中，建立僅用於協助偵錯的第二個暫時性服務。 您可以安裝這兩項服務，然後再啟動這個虛擬服務以載入服務處理序。 一旦暫時性服務啟動了處理序，您就可以使用 Visual Studio 中的 [偵錯] 功能表來附加至服務處理序。  
  
 嘗試加入對 <xref:System.Threading.Thread.Sleep%2A> 方法的呼叫，將動作延遲到能夠附加至處理序之後。  
  
 嘗試將程式變更為一般主控台應用程式。 若要執行這項操作，請依照下列方式重寫 `Main` 方法，以根據程式的啟動方式，將程式當做 Windows 服務或主控台應用程式來執行。  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>HOW TO：將 Windows 服務當作主控台應用程式來執行  
  
1.  將方法加入執行 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法的服務：  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  依照下列方式重寫 `Main` 方法：  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        if (Environment.UserInteractive)  
        {  
            MyNewService service1 = new MyNewService(args);  
            service1.TestStartupAndStop(args);  
        }  
        else  
        {  
            // Put the body of your old Main method here.  
        }  
    }
    ```  
  
3.  在專案屬性的 [應用程式] 索引標籤中，將 [輸出類型] 設定為 [主控台應用程式]。  
  
4.  選擇 [開始偵錯] (F5)。  
  
5.  若要再次將程式當做 Windows 服務來執行，請以適用於 Windows 服務的方式來安裝及啟動程式。 您不需要回復這些變更。  
  
 在某些情況下 (例如當您想要偵錯只在系統啟動時發生的問題時)，您必須使用 Windows 偵錯工具。 安裝[適用於 Windows 的偵錯工具](https://msdn.microsoft.com/windows/hardware/hh852365) \(英文\) 並參閱[如何對 Windows 服務進行偵錯](https://support.microsoft.com/kb/824344) \(機器翻譯\)。  
  
## <a name="see-also"></a>另請參閱
- [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [如何：安裝和解除安裝服務](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [如何：啟動服務](../../../docs/framework/windows-services/how-to-start-services.md)
- [對服務進行偵錯](/windows/desktop/Services/debugging-a-service) \(英文\)
