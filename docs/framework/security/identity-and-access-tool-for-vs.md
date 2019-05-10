---
title: Visual Studio 2012 的識別和存取工具
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: 999b85576c52d065075cad105c3212c1b034084f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626028"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a>Visual Studio 2012 的識別和存取工具
本主題說明適用於 Visual Studio 11 的新識別和存取工具。 您可以從下列 URL 下載此工具：<https://go.microsoft.com/fwlink/?LinkID=245849>或直接從 Visual Studio 11，藉由搜尋 「 識別 」，直接在延伸模組管理員中。  
  
 適用於 Visual Studio 11 的新識別和存取工具具有下列優點，可大幅簡化開發時間：  
  
- 使用這項新工具，您可以使用 Web 應用程式專案類型並以 IIS Express 為目標進行開發。  
  
- 這項新工具與僅具有保護功能的驗證方式不同，您可以指定本機主領域探索頁面/控制站 (或是在應用程式中處理驗證經驗的其他端點)，而 WIF 會將所有未驗證的要求都設定為移至該頁面/控制站，而不是將這些頁面重新導向至 STS。  
  
- 此工具包含測試 Security Token Service (STS)，當您啟動偵錯工作階段時，STS 隨即在您的本機電腦上執行。 因此，您不必再建立自訂和調整 STS 專案，就可以取得測試應用程式所需的宣告。 宣告類型和值都開放完全自訂。  
  
- 您可以直接透過工具的 UI 修改一般設定，而不必編輯 web.config。  
  
- 您可以在單一螢幕中，利用 Active Directory Federation Services (AD FS) 2.0 (或其他 WS-Federation 提供者) 建立同盟。  
  
- 此工具會利用簡單的核取方塊清單的 Windows Azure 存取控制服務 (ACS) 功能，您想要使用的所有身分識別提供者：Facebook、 Google、 Live ID、 yahoo ！、 所有 OpenID 提供者和任何 WS-同盟提供者。 只要選取識別提供者、按一下 [確定]，然後按 F5，您的應用程式和 ACS 即可自動設定完成，成為 ACS 感知測試應用程式。  
  
## <a name="see-also"></a>另請參閱

- [WIF 功能](../../../docs/framework/security/wif-features.md)
