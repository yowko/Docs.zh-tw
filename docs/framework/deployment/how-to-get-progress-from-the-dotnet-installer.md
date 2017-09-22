---
title: "如何：取得 .NET Framework 4.5 安裝程式的進度"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
caps.latest.revision: 30
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 404a092c6c05bcef568b234c9abeaf7969703cce
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：取得 .NET Framework 4.5 安裝程式的進度
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 為可轉散發執行階段。  如果您正在開發這個 .NET Framework 版本的應用程式，在應用程式設置中您可以將 \(chain\) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]設置包括至內做為必要條件元件。  若要呈現自訂或統一的安裝經驗，您可能會想要以無訊息模式啟動並追蹤 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝進度，同時顯示您應用程式的安裝進度。  若要啟用無訊息模式追蹤，[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]\(可檢視的\)設置會定義一個使用記憶體對應 I\/O \(MMIO\) 區段的通訊協定，來與您的設置\(監看員或 Chainer\)溝通 。  這個通訊協定定義 Chainer 取得進度、得到詳細結果、回應訊息以及取消 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 設置的方式。  
  
-   **引動過程**。若要呼叫 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 設置並從 MMIO 區段接收進度資訊，您的安裝程式必須執行以下動作：  
  
    1.  呼叫 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發程式:  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         其中 *section name* 是您想要用來識別您的應用程式之任意名稱。.NET Framework 設置會以非同步方式讀取和寫入 MMIO 區段，所以在這段期間事件和訊息的使用會很便利。  在範例中， .NET Framework 安裝程序是由配置 MMIO 區段的\(`TheSectionName`\) 和定義 \(`TheEventName`\)事件的建構函式所建立。  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         請使用對您的安裝程式獨特的名稱來取代這些名稱。  
  
    2.  從 MMIO 區段讀取。  在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，下載作業與安裝作業同時並行：當其中一部分 .NET Framework還在下載時，已經下載好的部分可能在安裝中。  因此，進度會以 兩個0 到 255 遞增數字\(`m_downloadSoFar` 及`m_installSoFar`\)的形式傳回 \(也就是寫入\) MMIO 區段。  當已經寫入 255且.NET Framework 結束時，表示安裝已完成。  
  
-   **結束代碼**。  以下來自呼叫[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發程式的命令所送出的結束代碼會指出安裝成功或失敗：  
  
    -   0 \- 已成功完成安裝。  
  
    -   3010 \-已成功完成安裝，需要重新啟動系統。  
  
    -   1602 \- 已取消安裝。  
  
    -   所有其他代碼 \- 安裝遇到錯誤，請檢查 %temp% 中所建立的記錄檔以找出詳細資訊。  
  
-   **取消安裝**。  您可以隨時取消安裝，其方式是使用 `Abort` 方法在 MMIO 區段中設定 `m_downloadAbort` 和 `m_ installAbort` 旗標。  
  
## Chainer 範例  
 Chainer 範例以無訊息模式啟動並追蹤 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 設置，同時也會顯示進度。  這個範例與 .NET Framework 4 所提供的 Chainer 範例相似。  不過此外，此範例也可以藉由處理關閉 .NET Framework 4 應用程式的訊息方塊，來避免系統重新啟動。  如需此對話方塊的詳細資訊，請參閱 [在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數](../../../docs/framework/deployment/reducing-system-restarts.md)。  您可以搭配 .NET Framework 4 安裝程式來使用這個範例；這種使用方式不會傳送訊息。  
  
> [!WARNING]
>  您必須以系統管理員身分執行此範例。  
  
 您可以從 MSDN 範例繪製廊下載完整的 Visual Studio [.NET Framework 4.5 Chainer 範例](http://go.microsoft.com/fwlink/?LinkId=231345) 方案。  
  
 以下幾段內容說明在此範例中的重要檔案:MMIOChainer.h、ChainingdotNet4.cpp 和 IProgressObserver.h。  
  
#### MmIoChainer.h  
  
-   MmIoChainer.h 檔案 \(請參閱[完整程式碼](http://go.microsoft.com/fwlink/?LinkId=231369)\) 包含來自Chainer 類別應衍生的資料結構定義與基底類別。  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 擴充 MMIO 資料結構以便於處理 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝程式所需的資料。   MMIO 結構的更新為回溯相容，因此 .NET Framework 4 Chainer不需要重新編譯即可在 .NET Framework 4.5的設置上正常運作。  不過，此案例不支援減少系統重新啟動次數的功能。  
  
     版本欄位提供辨識結構修訂和訊息格式修訂的方法。.NET Framework 設置藉由呼叫用來判斷檔案對應的大小的`VirtualQuery` 函式，來判別Chainer 介面的版本。如果大小足以容納版本欄位， .NET Framework 設置會使用指定值。  如果檔案對應太小而無法包含版本欄位，尤其是 .NET Framework 4 的情況下，安裝程序假設 0 版 \(4\)。  如果 Chainer 不支援.NET Framework 設置所要傳送訊息的版本，.NET Framework 設置會假設為忽略回應。  
  
     MMIO 資料結構定義如下：  
  
    ```cpp  
    // MMIO data structure for interprocess communication  
        struct MmioDataStructure  
        {  
            bool m_downloadFinished;               // Is download complete?  
            bool m_installFinished;                // Is installation complete?  
            bool m_downloadAbort;                  // Set to cause downloader to abort.  
            bool m_installAbort;                   // Set to cause installer to abort.  
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.  
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.  
            HRESULT m_hrInternalError;  
            WCHAR m_szCurrentItemStep[MAX_PATH];  
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).   
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).  
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.  
  
            BYTE m_version;                        // Version of the data structure, set by chainer:  
                                                   // 0x0: .NET Framework 4   
                                                   // 0x1: .NET Framework 4.5  
  
            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.  
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.  
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.  
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.  
        };  
  
    ```  
  
-   在實作 Chainer時不能直接使用 `MmioDataStructure` 資料結構，而是使用 `MmioChainer` 類別。  衍生自 `MmioChainer` 類別可散發地鏈結 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 。  
  
#### IprogressObserver.h  
  
-   IProgressObserver.h 檔案實作進度觀察器 \([如需完整程式碼](http://go.microsoft.com/fwlink/?LinkId=231370)\)。  觀察者取得下載和安裝進度的通知 \(指定為不帶正負號的 `char`， 0\-255，表示 1%\-100% 完整\)。  當 Chainee 傳送訊息時也會通知觀察者，而觀察者應該傳送回覆。  
  
    ```cpp  
        class IProgressObserver  
        {  
        public:  
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%  
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete    
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent  
        };  
  
    ```  
  
#### ChainingdotNet4.5.cpp  
  
-   [ChainingdotNet4.5.cpp](http://go.microsoft.com/fwlink/?LinkId=231368)檔案實作衍生自`MmioChainer` 類別、並覆寫適當方法以顯示進度資訊的`Server`類別。  MmioChainer 會以指定的區段名稱建立一個區段並以指定的事件名稱初始化Chainer。  事件名稱儲存在相對應的資料結構中。  您應該讓區段與事件名稱為獨特的。  下列程式碼中的 `Server` 類別會啟動指定的安裝程式、監控其進度並傳回結束代碼。  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
  
    ```  
  
     安裝在主要方法中啟動。  
  
    ```cpp  
    // Main entry point for program  
    int __cdecl main(int argc, _In_count_(argc) char **_argv)  
    {  
        int result = 0;  
        CString args;  
        if (argc > 1)  
        {  
            args = CString(_argv[1]);  
        }  
  
        if (IsNetFx4Present(NETFX45_RC_REVISION))  
        {  
            printf(".NET Framework 4.5 is already installed");  
        }  
        else  
        {  
            result = Server().Launch(args);  
        }  
  
        return result;  
    }  
  
    ```  
  
-   在啟動安裝之前，Chainer 會藉由呼叫 `IsNetFx4Present`，檢查是否已經安裝 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。  
  
    ```cpp  
    ///  Checks for presence of the .NET Framework 4.  
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full  
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.  
    #define NETFX40_FULL_REVISION 0  
    // TODO: Replace with released revision number  
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5   
    bool IsNetFx4Present(DWORD dwMinimumRelease)  
    {  
        DWORD dwError = ERROR_SUCCESS;  
        HKEY hKey = NULL;  
        DWORD dwData = 0;  
        DWORD dwType = 0;  
        DWORD dwSize = sizeof(dwData);  
  
        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);  
        if (ERROR_SUCCESS == dwError)  
        {  
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))  
            {  
                dwError = ERROR_INVALID_DATA;  
            }  
            else if (ERROR_FILE_NOT_FOUND == dwError)  
            {  
                // Release value was not found, let's check for 4.0.  
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
                // Install = (REG_DWORD)1;  
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))  
                {  
                    // treat 4.0 as Release = 0  
                    dwData = 0;  
                }  
                else  
                {  
                    dwError = ERROR_INVALID_DATA;  
                }  
            }  
        }  
  
        if (hKey != NULL)  
        {  
            ::RegCloseKey(hKey);  
        }  
  
        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));  
    }  
  
    ```  
  
-   您可以在 `Launch` 方法中將可執行檔 \(此範例中的 Setup.exe\)的路徑變更為指向它的正確位置，或是自訂程式碼來決定位置。  `MmioChainer` 基底類別提供一種衍生類別呼叫的阻擋 `Run()` 方法。  
  
    ```cpp  
  
    bool Launch(const CString& args)  
    {  
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run  
    STARTUPINFO si = {0};  
    si.cb = sizeof(si);  
    PROCESS_INFORMATION pi = {0};  
  
    // Launch the Setup.exe that installs the .NET Framework 4.5  
    BOOL bLaunchedSetup = ::CreateProcess(NULL,   
     cmdline.GetBuffer(),  
     NULL, NULL, FALSE, 0, NULL, NULL,   
     &si,  
     &pi);  
  
    // If successful   
    if (bLaunchedSetup != 0)  
    {  
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);  
    Run(pi.hProcess, observer);  
  
    ……………………..   
    return (bLaunchedSetup != 0);  
    }  
  
    ```  
  
-   `Send` 方法攔截訊息並處理之。在這個 .NET Framework 版本，唯一受支援的訊息是關閉應用程式的訊息。  
  
    ```cpp  
            // SendMessage  
            //  
            // Send a message and wait for the response.  
            // dwMessage: Message to send  
            // pData: The buffer to copy the data to  
            // dwDataLength: Initially a pointer to the size of pBuffer.  Upon successful call, the number of bytes copied to pBuffer.  
            //--------------------------------------------------------------  
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)  
        {  
            DWORD dwResult = 0;  
            printf("recieved message: %d\n", dwMessage);  
            // Handle message  
            switch (dwMessage)  
            {  
            case MMIO_CLOSE_APPS:  
                {  
                    printf("    applications are holding files in use:\n");  
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);  
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)  
                    {  
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);  
                    }  
  
                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");  
                    while (dwResult == 0)  
                    {  
                        switch (toupper(getwchar()))  
                        {  
                        case 'Y':  
                            dwResult = IDYES;  // Close apps  
                            break;  
                        case 'N':  
                            dwResult = IDNO;  
                            break;  
                        case 'R':  
                            dwResult = IDRETRY;  
                            break;  
                        }  
                    }  
                    printf("\n");  
                    break;  
                }  
            default:  
                break;  
            }  
            printf("  response: %d\n  ", dwResult);  
            return dwResult;  
        }  
    };  
  
    ```  
  
-   進度資料是 0 \(0%\)到 255\(100%\) 之間不帶正負號的 `char` 。  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
  
    ```  
  
-   HRESULT會被傳遞至 `Finished` 方法。  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
  
    ```  
  
    > [!IMPORTANT]
    >  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發程式通常會寫入許多進度訊息以及指示完成\(在 Chainer 端\)的單一訊息 。  它也會以非同步方式讀取，以尋找 `Abort` 記錄。  如果它收到 `Abort` 記錄，則會取消安裝，而且在安裝中止、安裝作業皆復原後，寫入 E\_ABORT資料到完成記錄中。  
  
 一個典型的伺服器會建立隨機的MMIO 檔案名稱、建立此檔案 \(如上一個程式碼範例的 `Server::CreateSection` 所示\)，並且會使用 `CreateProcess`，以及"`-pipe someFileSectionName`" 選項傳遞管道名稱，以這兩種來啟動可轉散發程式。  伺服器應該利用應用程式使用者介面特定的程式碼來實作 `OnProgress`、 `Send`和 `Finished` 方法。  
  
## 請參閱  
 [開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)   
 [部署](../../../docs/framework/deployment/net-framework-and-applications.md)