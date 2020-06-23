---
title: How to：使用 MMC 嵌入式管理單元來查看憑證
description: 安全的 WCF 用戶端或服務可以使用憑證做為認證。 瞭解您可以使用 MMC 外掛程式檢查的憑證存放區類型。
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: e63034e48ae836f67f89b454829f7196c94610cd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246671"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>How to：使用 MMC 嵌入式管理單元來查看憑證
當您建立安全的用戶端或服務時，您可以使用[憑證做為認證。](working-with-certificates.md) 例如，一般認證類型是您使用方法建立的 x.509 憑證 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> 。

您可以使用 Windows 系統上的 Microsoft Management Console （MMC）來檢查三種不同類型的憑證存放區：

- 本機電腦：此存放區位於裝置的本機，而且裝置上的所有使用者都是全域的。

- 目前的使用者：此存放區位於裝置上目前使用者帳戶的本機。

- 服務帳戶：此存放區位於裝置上的特定服務的本機。

## <a name="view-certificates-in-the-mmc-snap-in"></a>在 MMC 嵌入式管理單元中查看憑證

下列程式示範如何檢查本機裝置上的存放區，以尋找適當的憑證：
  
1. 從 [**開始**] 功能表中選取 [**執行**]，然後輸入*mmc*。

    MMC 隨即出現。
  
2. 從 [**檔案**] 功能表中，選取 [**新增/移除嵌入式管理單元**]。

    [**新增或移除嵌入式管理單元**] 視窗隨即出現。
  
3. 從 [**可用的嵌入式管理單元**] 清單中，選擇 [**憑證**]，然後選取 [**新增**]。  

    ![新增憑證嵌入式管理單元](./media/mmc-add-certificate-snap-in.png)
  
4. 在 [**憑證**] 嵌入式管理單元視窗中，選取 [**電腦帳戶**]，然後選取 **[下一步]**。
  
    （選擇性）您可以選取 [**我的使用者帳戶**]，以取得特定服務的目前使用者或**服務帳戶**。

    > [!NOTE]
    > 如果您不是裝置的系統管理員，則只能管理您的使用者帳戶的憑證。
  
5. 在 [**選取電腦**] 視窗中，保留選取 [**本機電腦**]，然後選取 **[完成]**。  
  
6. 在 [**新增或移除嵌入式管理單元**] 視窗中，選取 **[確定]**。  
  
    ![新增憑證嵌入式管理單元](./media/mmc-certificate-snap-in-selected.png)

7. 選擇性：**從 [檔案**] 功能表中，選取 [**儲存**] 或 [**另存**新檔] 以儲存 MMC 主控台檔案以供稍後使用。  

8. 若要在 MMC 嵌入式管理單元中查看憑證，請在左窗格中選取 [**主控台根目錄**]，然後展開 [**憑證（本機電腦）**]。

    每種憑證類型的目錄清單隨即出現。 您可以從每個憑證目錄中，查看、匯出、匯入和刪除其憑證。

## <a name="view-certificates-with-the-certificate-manager-tool"></a>使用憑證管理員工具來查看憑證

您也可以使用 [憑證管理員] 工具來查看、匯出、匯入和刪除憑證。

### <a name="to-view-certificates-for-the-local-device"></a>若要查看本機裝置的憑證

1. 從 [**開始**] 功能表中選取 [**執行**]，然後輸入*certlm.msc*。

    本機裝置的 [憑證管理員] 工具隨即出現。
  
2. 若要查看您的憑證，請在左窗格中的 [**憑證-本機電腦**] 底下，展開您要查看之憑證類型的目錄。

### <a name="to-view-certificates-for-the-current-user"></a>若要查看目前使用者的憑證

1. 從 [**開始**] 功能表中選取 [**執行**]，然後輸入*certmgr.msc*。

    目前使用者的 [憑證管理員] 工具隨即出現。
  
2. 若要查看您的憑證，請在左窗格中的 [**憑證-目前的使用者**] 底下，展開您要查看之憑證類型的目錄。

## <a name="see-also"></a>另請參閱

- [使用憑證](working-with-certificates.md)
- [如何：建立要在開發期間使用的暫時憑證](how-to-create-temporary-certificates-for-use-during-development.md)
- [如何：取出憑證的指紋](how-to-retrieve-the-thumbprint-of-a-certificate.md)
