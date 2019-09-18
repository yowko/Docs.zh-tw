---
title: 作法：取得 .NET Framework 4.5 安裝程式的進度
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdd2832f112706cef6050774ce3f6db5a940424a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052092"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a>作法：取得 .NET Framework 4.5 安裝程式的進度

.NET Framework 4.5 是可轉散發的執行階段。 如果您要開發這個 .NET Framework 版本的應用程式，可以在應用程式安裝程式中納入 (鏈結) .NET Framework 4.5 安裝程式作為必要條件。 若要呈現自訂或整合的安裝體驗，您可能要以無訊息模式啟動 .NET Framework 4.5 安裝程式並追蹤其進度，同時顯示應用程式的安裝進度。 若要啟用無訊息追蹤，.NET Framework 4.5 安裝程式 (您可加以監看) 會使用記憶體對應 I/O (MMIO) 區段定義通訊協定，以便與您的安裝程式 (監控程式或 Chainer) 進行通訊。 此通訊協定會定義一種方式讓 Chainer 獲得進度資訊、取得詳細結果、回應訊息，以及取消 .NET Framework 4.5 安裝程式。

- **引動過程**。 若要呼叫 .NET Framework 4.5 安裝程式並從 MMIO 區段接收進度資訊，您的安裝程式必須執行下列動作：

    1. 呼叫 .NET Framework 4.5 可轉散發程式：

        `dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name`

        「區段名稱」是您想要用來識別應用程式的任意名稱。 .NET Framework 安裝程式會以非同步方式讀寫 MMIO 區段，所以您可能會覺得在這段期間使用事件和訊息很方便。 在範例中，.NET Framework 安裝程序是由配置 MMIO 區段 (`TheSectionName`) 及定義事件 (`TheEventName`) 的建構函式所建立：

        ```cpp
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")
        ```

        請用對您安裝程式而言的唯一名稱來取代這些名稱。

    2. 讀取 MMIO 區段。 .NET Framework 4.5 的下載作業與安裝作業會同時進行：.NET Framework 的某一部分可能會進行安裝，另一個部分則進行下載。 因此，傳回 (也就是寫入) 至 MMIO 區段的進度是從 0 遞增到 255 的兩個數字 (`m_downloadSoFar` 和 `m_installSoFar`)。 當 255 寫入而 .NET Framework 結束時，安裝即已完成。

- **結束代碼** 呼叫 .NET Framework 4.5 可轉散發程式命令中的下列結束代碼會指出安裝成功或失敗：

  - 0 - 安裝順利完成。

  - 3010 – 安裝成功，需要重新啟動系統。

  - 1602 – 已取消安裝。

  - 所有其他代碼 - 安裝程式發生錯誤，詳細資料請檢查在 %temp%中建立的記錄檔。

- **取消安裝程式**。 您可以使用 `Abort` 方法設定 MMIO 區段中的 `m_downloadAbort` 和 `m_ installAbort` 旗標，隨時取消安裝程式。

## <a name="chainer-sample"></a>Chainer 範例

Chainer 範例會以無訊息模式啟動並追蹤 .NET Framework 4.5 安裝程式，同時顯示進度。 此範例類似為 .NET Framework 4 提供的 Chainer 範例。 但另外，它可以處理關閉 .NET Framework 4 應用程式的訊息方塊，避免系統重新啟動。 如需此訊息方塊的資訊，請參閱[在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數](reducing-system-restarts.md)。 您可以使用此範例配合 .NET Framework 4 安裝程式，在該案例中不會傳送訊息。

> [!WARNING]
> 您必須以系統管理員身分執行此範例。

您可以從 MSDN 範例庫下載適用於 [.NET Framework 4.5 Chainer 範例](https://go.microsoft.com/fwlink/?LinkId=231345)的完整 Visual Studio 方案。

以下各節會描述此範例中的重要檔案：MMIOChainer.h、ChainingdotNet4.cpp 和 IProgressObserver.h。

#### <a name="mmiochainerh"></a>MMIOChainer.h

- MMIOChainer.h 檔案 (請參閱[完整程式碼](https://go.microsoft.com/fwlink/?LinkId=231369)) 包含資料結構定義和基底類別 (Chainer 類別會從其中衍生)。 .NET Framework 4.5 會擴充 MMIO 資料結構以處理 .NET Framework 4.5 安裝程式需要的資料。 MMIO 結構的變更與舊版相容，因此 .NET Framework 4 Chainer 不需要重新編譯，即可使用 .NET Framework 4.5 安裝程式。 不過，本案例不支援減少系統重新啟動的功能。

    版本欄位會提供識別結構和訊息格式修訂的方法。 .NET Framework 安裝程式會呼叫 `VirtualQuery` 函式來判斷檔案對應的大小，以判斷 Chainer 介面的版本。 如果大小足以容納版本欄位，.NET Framework 安裝程式就會使用指定的值。 如果檔案對應太小無法包含版本欄位，也就是 .NET Framework 4 的情況，則安裝程序會假設版本 0 (4)。 如果 Chainer 不支援 .NET Framework 安裝程式想要傳送的訊息版本，.NET Framework 安裝程式會假設忽略回應。

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

- `MmioDataStructure` 資料結構不應直接使用，請改用 `MmioChainer` 類別實作您的 Chainer。 衍生自 `MmioChainer` 類別以鏈結 .NET Framework 4.5 可轉散發套件。

#### <a name="iprogressobserverh"></a>IProgressObserver.h

- IProgressObserver.h 檔案會實作進度觀察器 ([請參閱完整程式碼](https://go.microsoft.com/fwlink/?LinkId=231370))。 這個觀察器會收到下載和安裝進度通知 (指定為不帶正負號的 `char`，即 0-255，指出完成度 1%-100%)。 當 Chainee 傳送訊息時也會通知觀察器，而觀察器應該傳送回應。

    ```cpp
        class IProgressObserver
        {
        public:
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent
        };
    ```

#### <a name="chainingdotnet45cpp"></a>ChainingdotNet4.5.cpp

- 衍生自 `MmioChainer` 類別的 [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) 檔案會實作 `Server` 類別，並覆寫適當的方法以顯示進度資訊。 MmioChainer 會以指定的區段名稱建立區段，並以指定的事件名稱初始化 Chainer。 事件名稱會儲存在對應的資料結構中。 您應該使用唯一的區段和事件名稱。 下列程式碼中的 `Server` 類別會啟動指定的安裝程式、監視其進度，並傳回結束代碼。

    ```cpp
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver
    {
    public:
        …………….
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names
        {}
    ```

    安裝是在 Main 方法中啟動。

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

- 在啟動安裝之前，Chainer 會呼叫 `IsNetFx4Present` 來查看是否已安裝 .NET Framework 4.5：

    ```cpp
    ///  Checks for presence of the .NET Framework 4.
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.
    #define NETFX40_FULL_REVISION 0
    // TODO: Replace with released revision number
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5
    bool IsNetFx4Present(DWORD dwMinimumRelease)
    {
        DWORD dwError = ERROR_SUCCESS;
        HKEY hKey = NULL;
        DWORD dwData = 0;
        DWORD dwType = 0;
        DWORD dwSize = sizeof(dwData);

        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);
        if (ERROR_SUCCESS == dwError)
        {
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);

            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))
            {
                dwError = ERROR_INVALID_DATA;
            }
            else if (ERROR_FILE_NOT_FOUND == dwError)
            {
                // Release value was not found, let's check for 4.0.
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);

                // Install = (REG_DWORD)1;
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))
                {
                    // treat 4.0 as Release = 0
                    dwData = 0;
                }
                else
                {
                    dwError = ERROR_INVALID_DATA;
                }
            }
        }

        if (hKey != NULL)
        {
            ::RegCloseKey(hKey);
        }

        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));
    }
    ```

- 您可以在 `Launch` 方法中變更可執行檔路徑 (範例中為 Setup.exe)，指向正確的位置，或自訂程式碼來決定位置。 `MmioChainer` 基底類別提供衍生類別呼叫的封鎖 `Run()` 方法。

    ```cpp
    bool Launch(const CString& args)
    {
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run
    STARTUPINFO si = {0};
    si.cb = sizeof(si);
    PROCESS_INFORMATION pi = {0};

    // Launch the Setup.exe that installs the .NET Framework 4.5
    BOOL bLaunchedSetup = ::CreateProcess(NULL,
     cmdline.GetBuffer(),
     NULL, NULL, FALSE, 0, NULL, NULL,
     &si,
     &pi);

    // If successful
    if (bLaunchedSetup != 0)
    {
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);
    Run(pi.hProcess, observer);

    ……………………..
    return (bLaunchedSetup != 0);
    }
    ```

- `Send` 方法會攔截並處理訊息。 這個 .NET Framework 版本中唯一支援的訊息是關閉應用程式訊息。

    ```cpp
            // SendMessage
            //
            // Send a message and wait for the response.
            // dwMessage: Message to send
            // pData: The buffer to copy the data to
            // dwDataLength: Initially a pointer to the size of pBuffer. Upon successful call, the number of bytes copied to pBuffer.
            //--------------------------------------------------------------
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)
        {
            DWORD dwResult = 0;
            printf("received message: %d\n", dwMessage);
            // Handle message
            switch (dwMessage)
            {
            case MMIO_CLOSE_APPS:
                {
                    printf("    applications are holding files in use:\n");
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)
                    {
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);
                    }

                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");
                    while (dwResult == 0)
                    {
                        switch (toupper(getwchar()))
                        {
                        case 'Y':
                            dwResult = IDYES;  // Close apps
                            break;
                        case 'N':
                            dwResult = IDNO;
                            break;
                        case 'R':
                            dwResult = IDRETRY;
                            break;
                        }
                    }
                    printf("\n");
                    break;
                }
            default:
                break;
            }
            printf("  response: %d\n  ", dwResult);
            return dwResult;
        }
    };
    ```

- 進度資料是不帶正負號的 `char`，介於 0 (0%) 和 255 (100%) 之間。

    ```cpp
    private: // IProgressObserver
        virtual void OnProgress(unsigned char ubProgressSoFar)
        {…………
       }
    ```

- HRESULT 會傳遞至 `Finished` 方法。

    ```cpp
    virtual void Finished(HRESULT hr)
    {
    // This HRESULT is communicated over MMIO and may be different than process
    // Exit code of the Chainee Setup.exe itself
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);
    }
    ```

    > [!IMPORTANT]
    > 一般來說，.NET Framework 4.5 可轉散發套件會寫入許多進度訊息和表示完成的單一訊息 (在 Chainer 端上)。 它也會以非同步方式讀取，尋找 `Abort` 記錄。 如果收到 `Abort` 記錄，即取消安裝，並在中止安裝且復原安裝作業之後，以 E_ABORT 寫入完成記錄當成資料。

一般的伺服器會建立隨機的 MMIO 檔案名稱、建立檔案 (如先前 `Server::CreateSection` 的程式碼範例所示)，並使用 `CreateProcess` 方法以 `-pipe someFileSectionName` 選項傳遞管道名稱來啟動可轉散發套件。 伺服器應利用應用程式 UI 特定的程式碼實作 `OnProgress`、`Send` 和 `Finished` 方法。

## <a name="see-also"></a>另請參閱

- [開發人員部署手冊](deployment-guide-for-developers.md)
- [部署](index.md)
