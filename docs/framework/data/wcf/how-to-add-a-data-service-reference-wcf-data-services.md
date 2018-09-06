---
title: 如何：加入資料服務參考 (WCF 資料服務)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: fc1786e1c6102c702374989253cd3ce23e3f7b54
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44032393"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>如何： 加入資料服務參考 (WCF Data Services)

您可以使用**加入服務參考**對話方塊在 Visual Studio 中將參考加入至 WCF Data Services。 這樣可以讓您更輕鬆地在 Visual Studio 開發的用戶端應用程式中存取資料服務。 當您完成此程序時，會根據從資料服務取得的中繼資料產生資料類別。 如需詳細資訊，請參閱 <<c0> [ 產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)。

## <a name="add-a-data-service-reference"></a>加入資料服務參考

1. (選擇性) 如果資料服務不是方案的一部分且尚未執行，請啟動資料服務，並且記下資料服務的 URI。

2. 在 Visual Studio 中，在**方案總管**，以滑鼠右鍵按一下 用戶端專案，然後選取**新增** > **服務參考**。

3. 如果資料服務的目前方案的一部分，請按一下**探索**。

     -或-

     在 **地址**文字方塊中，輸入基底 URL 的資料服務，例如`http://localhost:1234/Northwind.svc`，然後按一下 **移**。

4. 選取 [確定]。

     包含可以存取和使用資料服務資源的資料類別的新程式碼檔案會加入至專案。

## <a name="see-also"></a>另請參閱

- [快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)