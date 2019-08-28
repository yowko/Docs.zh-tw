---
title: 在 SQL Server 中簽署預存程序
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: a30b5e28263c9f36e80c4e6b848033d5095b830b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043938"
---
# <a name="signing-stored-procedures-in-sql-server"></a>在 SQL Server 中簽署預存程序

數位簽章是指使用簽署者之私密金鑰 (Private Key) 加密的資料摘要。 私密金鑰可確保數位簽章對於其 Bearer 或擁有者而言是唯一的。 您可以簽署預存程式、函數 (內嵌資料表值函數除外)、觸發程式和元件。

您可以使用憑證或非對稱金鑰來簽署預存程序。 這是針對無法透過擁有權鏈結繼承權限或擁有權鏈結中斷 (例如動態 SQL) 的案例所設計。 接著, 您可以建立對應至憑證的使用者, 並授與預存程式需要存取之物件的憑證使用者權限。

您也可以建立對應至相同憑證的登入, 然後將任何必要的伺服器層級許可權授與該登入, 或將登入加入一個或多個固定伺服器角色。 這是為了避免在需要較`TRUSTWORTHY`高層級許可權的案例中啟用資料庫設定而設計的。

執行預存程式時, SQL Server 會將憑證使用者和/或登入的許可權與呼叫者結合。 與子句`EXECUTE AS`不同的是, 它不會變更程式的執行內容。 傳回登入和使用者名稱的內建函式會傳回呼叫端的名稱，而非憑證使用者名稱。

## <a name="creating-certificates"></a>建立憑證

當您使用憑證或非對稱金鑰來簽署預存程式時, 會使用私密金鑰來建立包含預存程式程式碼之加密雜湊和執行身分使用者的資料摘要。 在執行階段中，系統會使用公開金鑰 (Public Key) 來解密資料摘要，並與預存程序的雜湊值 (Hash Value) 進行比較。 變更 execute as 使用者會使雜湊值失效, 使數位簽章不再符合。 修改預存程式會完全卸載簽章, 這可防止沒有私密金鑰存取權的人變更預存程式程式碼。 不論是哪一種情況, 您都必須在每次變更程式碼或「執行身分」使用者時重新簽署程式。

簽署模組需要兩個必要步驟:

1. 使用 Transact-SQL `CREATE CERTIFICATE [certificateName]` 陳述式來建立憑證。 這個陳述式具有許多設定開始和結束日期與密碼的選項。 預設到期日為一年。

1. 使用 Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` 陳述式並搭配憑證來簽署程序。

簽署模組之後, 必須建立一或多個主體, 才能保存應與憑證相關聯的其他許可權。

如果模組需要其他資料庫層級的許可權:

1. 使用 Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` 陳述式來建立與憑證相關聯的資料庫使用者。 此使用者僅存在於資料庫中, 而且不會與登入相關聯, 除非已從該相同憑證建立登入。

1. 授與憑證使用者必要的資料庫層級許可權。

如果模組需要額外的伺服器層級許可權:

1. 將憑證複製到`master`資料庫。

1. 使用 transact-sql `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]`語句建立與該憑證相關聯的登入。

1. 授與憑證登入所需的伺服器層級許可權。

> [!NOTE]
> 憑證無法授與權限給擁有使用 DENY 陳述式撤銷之權限的使用者。 DENY 的優先順序永遠高於 GRANT，可防止呼叫端繼承授與憑證使用者的權限。

## <a name="external-resources"></a>外部資源

如需詳細資訊，請參閱下列資源。

|Resource|描述|
|--------------|-----------------|
|SQL Server 線上叢書中的[模組](https://go.microsoft.com/fwlink/?LinkId=98590)登入|說明模組簽署，並提供範例案例以及相關 Transact-SQL 主題的連結。|
|在 SQL Server 線上叢書中[使用憑證簽署預存程式](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate)|提供使用憑證來簽署預存程序的教學課程。|

## <a name="see-also"></a>另請參閱

- [設定 ADO.NET 應用程式的安全性](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server 安全性概觀](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [SQL Server 中的應用程式安全性案例](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [在 SQL Server 中使用預存程序來管理權限](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [在 SQL Server 中撰寫安全的動態 SQL](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [在 SQL Server 中使用模擬來自訂權限](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)
- [使用預存程序修改資料](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
