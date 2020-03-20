---
title: 如何：使用 MMC 卡入式查看證書
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184776"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>如何：使用 MMC 卡入式查看證書
創建安全用戶端或服務時，可以使用[證書](working-with-certificates.md)作為憑據。 例如，常用類型的憑據是 X.509 憑證，您可以使用 方法<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>創建該證書。

在 Windows 系統上可以使用 Microsoft 管理主控台 （MMC） 檢查三種不同類型的憑證存放區：

- 本地電腦：存儲是設備的本機存放區，並且對設備上的所有使用者是全域的。

- 當前使用者：存儲是設備上當前使用者帳戶的本機存放區。

- 服務帳戶：存儲是設備上特定服務的本機存放區。

## <a name="view-certificates-in-the-mmc-snap-in"></a>在 MMC 管理單元中查看證書

以下過程演示如何檢查本地設備上的存儲以查找適當的證書：
  
1. 選擇"從**開始"** 功能表**中運行**，然後輸入*mmc*。

    將顯示 MMC。
  
2. 從 **"檔**"功能表中，選擇 **"添加/刪除對齊入"。**

    將顯示 **"添加或刪除對齊"** 視窗。
  
3. 從 **"可用管理單元**"清單中，選擇 **"證書**"，然後選擇 **"添加**"。  

    ![添加證書管理單元](./media/mmc-add-certificate-snap-in.png)
  
4. 在 **"證書入駐"** 視窗中，選擇 **"電腦帳戶**"，然後選擇 **"下一步**"。
  
    或者，您可以選擇特定服務的當前使用者或服務**帳戶****的"我的使用者帳戶**"。

    > [!NOTE]
    > 如果您不是設備的管理員，則只能管理使用者帳戶的證書。
  
5. 在 **"選擇電腦"** 視窗中，保持**本地電腦**選中狀態，然後選擇 **"完成**"。  
  
6. 在 **"添加或刪除對齊"** 視窗中，選擇 **"確定**"。  
  
    ![添加證書管理單元](./media/mmc-certificate-snap-in-selected.png)

7. 可選：從 **"檔**"功能表中，選擇 **"保存****"或"保存為"** 以保存 MMC 主控台檔以供以後使用。  

8. 要在 MMC 管理單元中查看證書，請在左側窗格中選擇 **"主控台根"，** 然後展開**證書（本地電腦）。**

    將顯示每種類型的證書的目錄清單。 在每個證書目錄中，您可以查看、匯出、導入和刪除其證書。

## <a name="view-certificates-with-the-certificate-manager-tool"></a>使用證書管理器工具查看證書

您還可以使用證書管理器工具查看、匯出、導入和刪除證書。

### <a name="to-view-certificates-for-the-local-device"></a>查看本地設備的證書

1. 選擇"**從開始"** 功能表**中運行**，然後輸入*certlm.msc*。

    將顯示本地設備的證書管理器工具。
  
2. 要查看證書，在左側窗格中的 **"證書 - 本地電腦**"下，請展開要查看的證書類型的目錄。

### <a name="to-view-certificates-for-the-current-user"></a>查看當前使用者的證書

1. 選擇"**從開始"** 功能表**中運行**，然後輸入*certmgr.msc*。

    將顯示當前使用者的證書管理器工具。
  
2. 要查看證書，在左側窗格中的 **"證書 - 當前使用者**"下，請展開要查看的證書類型的目錄。

## <a name="see-also"></a>另請參閱

- [使用證書](working-with-certificates.md)
- [如何：創建臨時證書，供開發期間使用](how-to-create-temporary-certificates-for-use-during-development.md)
- [如何：檢索證書的指紋](how-to-retrieve-the-thumbprint-of-a-certificate.md)
