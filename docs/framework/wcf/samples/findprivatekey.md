---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81ca357ccdcbe76f36f3ba56caf2013a80143728
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="findprivatekey"></a>FindPrivateKey
在憑證存放區中尋找與特定 X.509 憑證相關聯的私密金鑰檔案位置和名稱，可能相當困難。 FindPrivateKey.exe 工具有助於進行這個程序。  
  
> [!IMPORTANT]
>  FindPrivateKey 是必須先編譯才能使用的範例。 如何建置 FindPrivateKey 工具，請參閱 < 若要建置 FindPrivateKey 專案 「 下一節的指示。  
  
 X.509 憑證是由電腦中的系統管理員或任何使用者所安裝。 然而，憑證可能由不同帳戶 (例如 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上的 ASPNET 或 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 上的 NETWORK SERVICE 帳戶) 下執行的服務存取。  
  
 這個帳戶可能無法用來存取私密金鑰檔案，因為憑證原先並非透過這個帳戶來安裝。 FindPrivateKey 工具提供您指定之 X.509 憑證的私密金鑰檔案位置。 一旦知道特定 X.509 憑證的私密金鑰檔案位置之後，您就可以新增權限至此檔案或移除此檔案的權限。  
  
 基於安全性而使用憑證的範例採用 Setup.bat 檔案中的 FindPrivateKey 工具。 一旦找到私密金鑰檔案，您就可以使用如 Cacls.exe 等其他工具，為檔案設定適當的存取權限。  
  
 在使用者帳戶下執行 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時 (例如自我裝載的可執行檔)，請確定使用者帳戶具有檔案的唯讀權限。 在網際網路資訊服務 (IIS) 下執行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務時，服務執行所在的預設帳戶為 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上的 ASPNET 或 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 上的 NETWORK SERVICE，該帳戶根據預設無法存取私密金鑰檔案。  
  
## <a name="examples"></a>範例  
 存取處理序沒有讀取權限的憑證時，您會看到類似下列範例的例外狀況訊息。  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 發生這種情況時，請使用 FindPrivateKey 工具尋找私密金鑰檔案，然後為服務執行所在的處理序設定存取權限。 例如，使用 Cacls.exe 工具完成此操作，如下列範例所示。  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a>若要建置 FindPrivateKey 專案  
  
1.  開啟 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]，並巡覽至安裝範例所在目錄位置下的語言特定子目錄。  
  
2.  按兩下 .sln 檔案圖示，在 Visual Studio 中開啟檔案。  
  
3.  在**建置**功能表上，選取**重建方案**。 用戶端程式檔會建置至 client\bin，服務程式檔則建置至 service\bin。  
  
4.  建置方案會產生檔案 FindPrivateKey.exe。  
  
## <a name="conventionscommand-line-entries"></a>慣例—命令列項目  
 "[*選項*]"代表一組選擇性的參數。  
  
 "{*選項*}"代表強制的參數組。  
  
 「*選項 1* &#124;*選項 2*"表示的選項集之間的選擇。  
  
 「\<*值*> 」 表示輸入參數值。  
  
## <a name="usage"></a>使用方式  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 其中：  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 如果未在命令提示字元中指定參數，則會顯示此說明文字。  
  
## <a name="examples"></a>範例  
 這個範例會在 Current User.FindPrivateKey My CurrentUser -n "CN=localhost" 的 Personal 存放區中尋找主體名稱為 "CN=localhost" 之憑證的檔案名稱。  
  
 這個範例會在 Current 的 Personal 存放區中尋找主體名稱為 "CN=localhost" 之憑證的檔案名稱，並且輸出完整的目錄路徑。  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 這個範例會在 Local Computer 的 Personal 存放區中尋找指紋為 "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" 之憑證的檔案名稱。  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a>另請參閱
