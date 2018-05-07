---
title: HOW TO：使用 MMC 嵌入式管理單元來檢視憑證
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: d924121b9d9fa267fa7d1ada13c9dc5f5bf1523d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>HOW TO：使用 MMC 嵌入式管理單元來檢視憑證
常見的認證類型是 X.509 憑證。 當建立安全服務或用戶端時，您可以藉由使用像是 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法，指定用來當做用戶端或服務認證的憑證。 方法需要各種參數，例如儲存憑證的存放區，以及當搜尋憑證時要使用的值。 下列程序示範如何檢視電腦上的存放區，以尋找適當的憑證。 尋找憑證指紋的範例，請參閱[How to： 擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>在 MMC 嵌入式管理單元中檢視憑證  
  
1.  開啟 [命令提示字元] 視窗。  
  
2.  型別`mmc`按下 ENTER 鍵。 請注意，若要檢視本機電腦存放區中的憑證，您必須是系統管理員的角色。  
  
3.  在**檔案**功能表上，按一下 **新增/移除嵌入式管理單元**。  
  
4.  按一下 [加入] 。  
  
5.  在**新增獨立嵌入式管理單元**對話方塊中，選取**憑證**。  
  
6.  按一下 [加入] 。  
  
7.  在**憑證嵌入式管理單元**對話方塊中，選取**電腦帳戶**按一下**下一步**。 或者，您可以選取**我的使用者帳戶**或**服務帳戶**。 如果您不是電腦的系統管理員，就只能夠管理您使用者帳戶的憑證。  
  
8.  在**選取電腦**對話方塊中，按一下 **完成**。  
  
9. 在**新增獨立嵌入式管理單元**對話方塊中，按一下 **關閉**。  
  
10. 在**新增/移除嵌入式管理單元**對話方塊中，按一下 **確定**。  
  
11. 在**主控台根目錄**視窗中，按一下 **憑證 （本機電腦）**以檢視憑證存放區的電腦。  
  
12. 選擇性。 若要檢視您帳戶的憑證，請重複步驟 3 到 6。 在步驟 7，而不是選取**電腦帳戶**，按一下 **我的使用者帳戶**並重複步驟 8 到 10。  
  
13. 選擇性。 在**檔案**功能表上，按一下 **儲存**或**存**。 儲存主控台檔案供稍後使用。  
  
## <a name="viewing-certificates-with-internet-explorer"></a>使用 Internet Explorer 檢視憑證  
 您也可以使用 Internet Explorer 檢視、匯出、匯入和刪除憑證。  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>使用 Internet Explorer 檢視憑證  
  
1.  在 Internet Explorer 中，按一下**工具**，然後按一下 [**網際網路選項**顯示**網際網路選項**] 對話方塊。  
  
2.  按一下**內容** 索引標籤。  
  
3.  在下**憑證**，按一下 **憑證**。  
  
4.  若要檢視任何憑證的詳細資料、 選取憑證按一下**檢視**。  
  
## <a name="see-also"></a>另請參閱  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [如何：建立開發時要使用的暫時憑證](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [如何：擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
