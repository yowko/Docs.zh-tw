---
title: HOW TO：使用 MMC 嵌入式管理單元檢視憑證
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 69f79b64250ff46524e7b4720d13351774875a3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167501"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>HOW TO：使用 MMC 嵌入式管理單元檢視憑證
當您建立安全的用戶端或服務時，您可以使用[憑證](working-with-certificates.md)身分的認證。 例如，常見的認證類型是 X.509 憑證，您建立與<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>方法。 

有三種不同的類型，您可以檢查與 Microsoft Management Console (MMC) 在 Windows 系統上的憑證存放區：

- 本機電腦：本機裝置和裝置上的所有使用者通用存放區。

- 目前的使用者：存放區是目前的使用者帳戶，在裝置上的本機。

- 服務帳戶：存放區是在裝置上的特定服務的本機。

## <a name="view-certificates-in-the-mmc-snap-in"></a>在 MMC 嵌入式管理單元檢視憑證 

下列程序示範如何檢查在您的本機裝置，以尋找適當的憑證存放區： 
  
1. 選取 **執行**從**開始**功能表，然後輸入*mmc*。 

    MMC 隨即出現。 
  
2. 從**檔案**功能表上，選取**新增/移除嵌入式管理單元**。 
    
    **新增或移除嵌入式管理單元** 視窗隨即出現。
  
3. 從**可用的嵌入式管理單元**清單中，選擇**憑證**，然後選取**新增**。  

    ![新增憑證嵌入式管理單元](./media/mmc-add-certificate-snap-in.png)
  
4. 在 [**憑證嵌入式管理單元**視窗中，選取**電腦帳戶**，然後選取**下一步]**。 
  
    或者，您可以選取**我的使用者帳戶**目前的使用者或**服務帳戶**針對特定服務。 

    > [!NOTE]
    > 如果您不是為您的裝置系統管理員，您可以只針對您的使用者帳戶來管理憑證。
  
5. 在 [**選取電腦**] 視窗中，保持**本機電腦**選取，然後按**完成**。  
  
6. 在 **新增或移除嵌入式管理單元**視窗中，選取**確定**。  
  
    ![新增憑證嵌入式管理單元](./media/mmc-certificate-snap-in-selected.png)

7. 選擇項：從**檔案**功能表上，選取**儲存**或是**另存新檔**儲存 MMC 主控台檔案供稍後使用。  

8. 若要檢視您的憑證 MMC 嵌入式管理單元中，選取**主控台根目錄**的左窗格中，然後展開**Certificates (Local Computer)**。

    每種類型的憑證的目錄清單隨即出現。 從每個憑證目錄中，您可以檢視、 匯出、 匯入，並刪除其憑證。

## <a name="view-certificates-with-the-certificate-manager-tool"></a>使用憑證管理員工具檢視憑證

您也可以檢視、 匯出、 匯入，並使用憑證管理員工具來刪除憑證。

### <a name="to-view-certificates-for-the-local-device"></a>若要檢視本機裝置的憑證

1. 選取 **執行**從**開始**功能表，然後輸入*certlm.msc*。 

    憑證管理員工具的本機裝置會出現。 
  
2. 若要檢視您的憑證，在**憑證-本機電腦**在左窗格中，依序展開您想要檢視的憑證類型的目錄。

### <a name="to-view-certificates-for-the-current-user"></a>若要檢視目前的使用者憑證

1. 選取 **執行**從**開始**功能表，然後輸入*certmgr.msc*。 

    目前使用者的憑證管理員工具隨即出現。 
  
2. 若要檢視您的憑證，在**憑證-目前使用者**在左窗格中，依序展開您想要檢視的憑證類型的目錄。

## <a name="see-also"></a>另請參閱

- [使用憑證](working-with-certificates.md)
- [HOW TO：建立開發時要使用的暫時憑證](how-to-create-temporary-certificates-for-use-during-development.md)
- [HOW TO：擷取憑證的指紋](how-to-retrieve-the-thumbprint-of-a-certificate.md)
