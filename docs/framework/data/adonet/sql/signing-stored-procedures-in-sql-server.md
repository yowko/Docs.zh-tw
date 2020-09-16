---
title: 在 SQL Server 中簽署預存程序
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 3f33af0238781407dd845a823ff28d87af48feb2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558546"
---
# <a name="signing-stored-procedures-in-sql-server"></a>在 SQL Server 中簽署預存程序

數位簽章是指使用簽署者之私密金鑰 (Private Key) 加密的資料摘要。 私密金鑰可確保數位簽章對於其 Bearer 或擁有者而言是唯一的。 您可以簽署預存程式、函式 (，但內嵌資料表值函式) 、觸發程式和元件除外。

您可以使用憑證或非對稱金鑰來簽署預存程序。 這是針對無法透過擁有權鏈結繼承權限或擁有權鏈結中斷 (例如動態 SQL) 的案例所設計。 然後，您可以建立對應至憑證的使用者，將預存程式需要存取之物件的許可權授與憑證使用者。

您也可以建立對應至相同憑證的登入，然後將所需的伺服器層級許可權授與該登入，或將登入加入至一或多個固定伺服器角色。 這是為了避免在 `TRUSTWORTHY` 需要較高層級許可權的情況下啟用資料庫設定的目的。

當執行預存程式時，SQL Server 會將憑證使用者和/或登入的許可權與呼叫端的許可權結合在一起。 和子句不同的是 `EXECUTE AS` ，它不會變更程式的執行內容。 傳回登入和使用者名稱的內建函式會傳回呼叫端的名稱，而非憑證使用者名稱。

## <a name="creating-certificates"></a>建立憑證

當您使用憑證或非對稱金鑰簽署預存程式時，系統會使用私密金鑰來建立包含預存程式程式碼的加密雜湊以及執行為使用者的資料摘要。 在執行階段中，系統會使用公開金鑰 (Public Key) 來解密資料摘要，並與預存程序的雜湊值 (Hash Value) 進行比較。 變更 execute as 使用者會讓雜湊值失效，使數位簽章不再相符。 修改預存程式會完全卸載簽章，這可防止沒有私密金鑰存取權的人員變更預存程式程式碼。 無論是哪一種情況，您都必須在每次變更程式碼或執行為使用者時重新簽署程式。

簽署模組有兩個必要步驟：

1. 使用 Transact-SQL `CREATE CERTIFICATE [certificateName]` 陳述式來建立憑證。 這個陳述式具有許多設定開始和結束日期與密碼的選項。 預設的到期日是一年。

1. 使用 Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]` 陳述式並搭配憑證來簽署程序。

一旦將模組簽署之後，必須建立一或多個主體，才能保存應該與憑證相關聯的其他許可權。

如果模組需要額外的資料庫層級許可權：

1. 使用 Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]` 陳述式來建立與憑證相關聯的資料庫使用者。 此使用者僅存在於資料庫中，除非也已經從相同的憑證建立登入，否則不會與登入相關聯。

1. 授與憑證使用者所需的資料庫層級許可權。

如果模組需要額外的伺服器層級許可權：

1. 將憑證複製到 `master` 資料庫。

1. 使用 Transact-sql 語句建立與該憑證相關聯的登入 `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]` 。

1. 授與憑證登入所需的伺服器層級許可權。

> [!NOTE]
> 憑證無法授與權限給擁有使用 DENY 陳述式撤銷之權限的使用者。 DENY 的優先順序永遠高於 GRANT，可防止呼叫端繼承授與憑證使用者的權限。

## <a name="external-resources"></a>外部資源

如需詳細資訊，請參閱下列資源。

|資源|描述|
|--------------|-----------------|
|[模組簽署](/previous-versions/sql/sql-server-2008/ms345102(v=sql.100))|描述模組簽署，提供範例案例和相關 Transact-sql 文章的連結。|
|[使用憑證簽署預存程序](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate)|提供使用憑證來簽署預存程序的教學課程。|

## <a name="see-also"></a>另請參閱

- [設定 ADO.NET 應用程式的安全性](../securing-ado-net-applications.md)
- [SQL Server 安全性概觀](overview-of-sql-server-security.md)
- [SQL Server 中的應用程式安全性案例](application-security-scenarios-in-sql-server.md)
- [使用預存程序管理 SQL Server 中的權限](managing-permissions-with-stored-procedures-in-sql-server.md)
- [在 SQL Server 撰寫安全動態 SQL](writing-secure-dynamic-sql-in-sql-server.md)
- [在 SQL Server 中使用模擬來自訂權限](customizing-permissions-with-impersonation-in-sql-server.md)
- [使用預存程序修改資料](../modifying-data-with-stored-procedures.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
