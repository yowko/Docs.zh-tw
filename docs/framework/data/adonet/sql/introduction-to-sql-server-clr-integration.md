---
title: SQL Server CLR 整合簡介
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: 215230486cb3e1ebee4cb40280b91c8bf9f6c799
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714928"
---
# <a name="introduction-to-sql-server-clr-integration"></a>SQL Server CLR 整合簡介
做為 Microsoft .NET Framework 核心的 Common Language Runtime (CLR)，提供了所有 .NET Framework 程式碼的執行環境。 CLR 中執行的程式碼稱為 Managed 程式碼。 CLR 提供程式執行所需的各種功能及服務，包括 just-in-time (JIT) 編譯、配置及管理記憶體、強制使用型別安全性、例外處理、執行緒管理及安全性。  
  
 利用 Microsoft SQL Server 中裝載的 CLR (稱為 CLR 整合)，您能夠以 Managed 程式碼撰寫預存程序、觸發程序、使用者定義函式、使用者定義型別及使用者定義彙總。 因為 Managed 程式碼在執行前會編譯成原生程式碼，所以在部分案例中可大幅提升效能。  
  
 Managed 程式碼使用程式碼存取安全性 (CAS)、程式碼連結及應用程式定義域，以防止組件執行某些作業。 SQL Server 使用 CAS 協助保護 Managed 程式碼，並防止損害作業系統或資料庫伺服器。  
  
 本節的目的是僅提供以 SQL Server CLR 整合進行程式設計快速入門所需的足夠資訊，並未包含廣泛資訊。 如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 線上叢書**  
  
-   [Common Language Runtime (CLR) 整合概觀](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a>啟用 CLR 整合  
 預設會在 Microsoft SQL Server 中停用 Common Language Runtime (CLR) 整合功能，且為了使用 CLR 整合所實作的物件，必須啟用這個功能。 若要啟用使用 Transact-SQL 進行 CLR 整合，請使用 `clr enabled` 預存程序的 `sp_configure` 選項，如下所示：  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 您可以將 `clr enabled` 選項設定為 0，藉以停用 CLR 整合。 停用 CLR 整合時，SQL Server 會停止執行所有 CLR 常式，並卸載所有應用程式定義域。  
  
 如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 線上叢書**  
  
-   [啟用 CLR 整合](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a>部署 CLR 組件  
 一旦 CLR 方法已經在測試伺服器上測試並驗證，您就可以使用部署指令碼，將它們散發至實際執行伺服器 (Production Server)。 您可以手動產生部署指令碼，也可以使用 SQL Server Management Studio 來產生部署指令碼。 如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 線上叢書**  
  
1.  [部署 CLR 資料庫物件](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a>CLR 整合安全性  
 Microsoft SQL Server 與 Microsoft .NET Framework Common Language Runtime (CLR) 的整合安全性模型，可管理及保護在 SQL Server 內執行之不同類型 CLR 及非 CLR 物件的存取權。 這些物件可由 Transact-SQL 陳述式或在伺服器中執行的其他 CLR 物件呼叫。  
  
 如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 線上叢書**  
  
-   [CLR 整合安全性](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a>偵錯 CLR 組件  
 Microsoft SQL Server 支援在資料庫中偵錯 Transact-SQL 及 Common Language Runtime (CLR) 物件。 偵錯可跨語言運作：使用者可以從 Transact-SQL 無接縫地進入 CLR 物件，反之亦然。  
  
 如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。  
  
 **SQL Server 線上叢書**  
  
-   [偵錯 CLR 資料庫物件](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a>另請參閱
- [在 Managed 程式碼中建立 SQL Server 2005 物件](https://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)
- [程式碼存取安全性和 ADO.NET](../../../../../docs/framework/data/adonet/code-access-security.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
