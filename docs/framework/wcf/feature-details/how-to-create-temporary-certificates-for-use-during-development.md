---
title: "HOW TO：建立開發時要使用的暫時憑證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a1b386906c1d493a23d8a58f3540758d3ae0d26e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>HOW TO：建立開發時要使用的暫時憑證
當使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]開發安全的服務或用戶端時，常常必須提供要用來做為認證的 X.509 憑證。 憑證通常是憑證鏈結的一部分，在電腦的 [受信任的根憑證授權單位] 存放區中有根授權。 具有憑證鏈結可讓您設定一組憑證的範圍，其中根授權通常來自您的組織或企業單位。 如果要在開發期間進行模擬，您可以建立兩種憑證以滿足安全性需求。 第一種是放在 [受信任的根憑證授權單位] 存放區中的自我簽署憑證，而第二種憑證是從第一種建立的，並放在個人存放區或本機位置，或目前使用者位置的個人存放區。 本主題將逐步帶領您使用由 [SDK 所提供的](http://go.microsoft.com/fwlink/?LinkId=248185)憑證建立工具 (MakeCert.exe) [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 來建立這兩種憑證。  
  
> [!IMPORTANT]
>  憑證建立工具所產生的憑證僅針對測試用途提供。 當部署服務或用戶端時，請確定使用由憑證授權單位所提供的適當憑證。 這可能是來自您組織中的 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 憑證伺服器或協力廠商。  
>   
>  根據預設， [Makecert.exe （憑證建立工具）](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)建立的憑證的根授權稱為 「 根代理者**。 」** 由於「根代理者」不是在 [受信任的根憑證授權單位] 存放區中，因此會讓這些憑證變得不安全。 建立位於 [受信任的根憑證授權單位] 存放區中的自我簽署憑證，可讓您建立一個更能夠模擬您開發環境的開發環境。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 建立及使用憑證的詳細資訊，請參閱 [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 使用憑證做為認證的詳細資訊，請參閱 [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)。 如需有關使用 Microsoft Authenticode 技術的教學課程，請參閱 [Authenticode 概觀與教學課程 (英文)](http://go.microsoft.com/fwlink/?LinkId=88919)。  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>建立自我簽署根授權憑證及匯出私密金鑰  
  
1.  請使用 MakeCert.exe 工具搭配下列參數：  
  
    1.  `-n` `subjectName`. 指定主體名稱。 慣例是使用 "CN = " 做為主體名稱的前置詞，代表「一般名稱」。  
  
    2.  `-r`. 指定憑證為自我簽署的。  
  
    3.  `-sv` `privateKeyFile`. 指定含有私密金鑰容器的檔案。  
  
     例如，下列命令會建立主體名稱為 "CN=TempCA" 的自我簽署憑證。  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     您會收到提供密碼以保護私密金鑰的提示。 當建立由這個根憑證簽署的憑證時，需要這個密碼。  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>建立由根授權憑證簽署的新憑證  
  
1.  請使用 MakeCert.exe 工具搭配下列參數：  
  
    1.  `-sk` `subjectKey`. 主體的金鑰容器的位置，其中包含私密金鑰。 如果金鑰容器不存在，便會建立一個。 如果 -sk 和 -sv 選項均未使用，根據預設，便會建立稱為 JoeSoft 的金鑰容器。  
  
    2.  `-n` `subjectName`. 指定主體名稱。 慣例是使用 "CN = " 做為主體名稱的前置詞，代表「一般名稱」。  
  
    3.  `-iv` `issuerKeyFile`. 指定簽發者的私密金鑰檔。  
  
    4.  `-ic` `issuerCertFile`. 指定簽發者的憑證的位置。  
  
     例如，下列命令會使用簽發者的私密金鑰，建立由主體名稱為 `TempCA` 的 `"CN=SignedByCA"` 根授權憑證簽署的憑證。  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>在受信任的根憑證授權單位存放區中安裝憑證  
 在建立自我簽署憑證之後，您就可以將它安裝在 [受信任的根憑證授權單位] 存放區中。 此時任何使用憑證簽署的憑證都受到電腦的信任。 因此，當您不再需要憑證時，請立刻從存放區中將其刪除。 當您刪除這個根授權憑證時，使用該憑證簽署的所有其他憑證都會變成未經授權的。 根授權憑證只是一種機制，可依需要設定一組憑證的範圍。 例如，在對等應用程式中，通常不需要根授權，因為您只是藉由個體提供的憑證而信任其身分識別。  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>在受信任的根憑證授權單位中安裝自我簽署憑證  
  
1.  請開啟憑證嵌入式管理單元。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][如何： 檢視憑證 MMC 嵌入式管理單元](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。  
  
2.  開啟資料夾以儲存憑證，可以是 [ **本機電腦** ] 或 [ **目前使用者**]。  
  
3.  開啟 [ **受信任的根憑證授權單位** ] 資料夾。  
  
4.  用滑鼠右鍵依序按一下 [ **憑證** ] 資料夾、[ **所有工作**] 和 [ **匯入**]。  
  
5.  請依照螢幕上的精靈指示，將 TempCa.cer 匯入存放區中。  
  
## <a name="using-certificates-with-wcf"></a>搭配 WCF 使用憑證  
 設定暫時憑證之後，您可以用它來開發可將憑證指定為用戶端認證類型的 WCF 方案。 例如，下列 XML 組態會指定訊息安全性，而且將憑證指定為用戶端認證類型。  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>若要將憑證指定為用戶端認證類型  
  
-   在服務的組態檔中，使用下列 XML 將安全性模式設定為訊息，而且將用戶端認證類型設定為憑證。  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 在用戶端組態檔中，使用下列 XML 指定憑證位於使用者的存放區，而且可以找到 SubjectName 欄位中搜尋值"CohoWinery"。  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 如需在 WCF 中使用憑證的詳細資訊，請參閱 [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 請用滑鼠右鍵按一下憑證，然後按一下 [ **刪除** ]，以確定從 [ **受信任的根憑證授權單位** ] 和 [ **個人**] 資料夾中刪除暫時的根授權憑證。  
  
## <a name="see-also"></a>另請參閱  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [如何： 檢視憑證 MMC 嵌入式管理單元](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [保護服務和用戶端](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
