---
title: 自訂作業：總覽
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: d4d375716e3199afcbbb9bbd8b8b04867ca0e5fa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173519"
---
# <a name="customizing-operations-overview"></a>自訂作業：總覽

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設會根據對應產生動態 SQL，以便進行插入、更新和刪除作業。 但實際上，您通常會想加入自己的業務邏輯，為安全性、驗證等做準備。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 自訂這些作業的技術包括下列各項。  
  
## <a name="loading-options"></a>載入選項  

 在查詢中，您可以控制在您連接至資料庫時要擷取多少與主要目標相關的資料。 這項功能大部分是使用 <xref:System.Data.Linq.DataLoadOptions> 來實作。 如需詳細資訊，請參閱 [延後和立即載入](deferred-versus-immediate-loading.md)。  
  
## <a name="partial-methods"></a>部分方法  

 在其預設對應中，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供了部分方法來協助您實作商務邏輯。 如需詳細資訊，請參閱 [使用部分方法加入商務邏輯](adding-business-logic-by-using-partial-methods.md)。  
  
## <a name="stored-procedures-and-user-defined-functions"></a>預存程序和使用者定義的函式  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援使用預存程式和使用者定義函數。 預存程序時常用於自訂作業。 如需詳細資訊，請參閱[預存程序](stored-procedures.md)。  
  
## <a name="see-also"></a>另請參閱

- [自訂插入、更新和刪除作業](customizing-insert-update-and-delete-operations.md)
