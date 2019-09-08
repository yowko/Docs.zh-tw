---
title: .NET Framework Data Provider for Oracle 的系統需求
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: 330bad6f58b1ba6b0d2fdb2baa86a04374946e80
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780585"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>.NET Framework Data Provider for Oracle 的系統需求
Oracle 的 .NET Framework 資料提供者需要 Microsoft Data Access Components (MDAC) 2.6 (含) 以後版本。 建議使用 MDAC 2.8 SP1。  
  
 您也必須安裝 Oracle 8i 第 3 版 (8.1.7) 用戶端 (含) 以後版本。  
  
 Oracle 9i 版之前的 Oracle 用戶端軟體無法存取 UTF16 資料庫，因為 UTF16 是 Oracle 9i 的新功能。 若要使用此功能，您必須將用戶端軟體升級至 Oracle 9i (含) 以後版本。  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>使用 Oracle 及 Unicode 資料的資料提供者  
 當您在使用 Oracle 的 .NET Framework 資料提供者及 Oracle 用戶端程式庫時，應該考量下列的 Unicode 相關問題清單。 如需詳細資訊，請參閱 Oracle 文件。  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>設定連接字串屬性中的 Unicode 值  
 使用 Oracle 時，您可以使用連接字串屬性  
  
```  
Unicode=True   
```  
  
 以 UTF-16 模式初始化 Oracle 用戶端程式庫。 這會導致 Oracle 用戶端程式庫接受 UTF-16 (與 UCS-2 非常類似)，而不接受多位元組的字串。 這可讓 Oracle 的資料提供者一律使用 Oracle 字碼頁，而無需進行其他轉譯工作。 僅在您使用 Oracle 9i 用戶端與具有 AL16UTF16 替代字元集的 Oracle 9i 資料庫通訊時，此組態才會運作。 當 Oracle 9i 用戶端與 Oracle 9i 伺服器通訊時，需要額外的資源，才能將 Unicode **CommandText**值轉換成 Oracle9i 伺服器所使用的適當多位元組字元集。 如果您知道將 `Unicode=True` 加入連接字串會得到安全的組態，便可避免此問題。  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Oracle 用戶端及 Oracle 伺服器的混合版本  
 將伺服器的國家字元集指定為 AL16UTF16 （Oracle 9i 的預設設定）時，oracle 8i 用戶端無法存取 Oracle 9i 資料庫中的**NCHAR**、 **NVARCHAR2**或**NCLOB**資料。 因為 Oracle 9i 之前的版本未引入對 UTF-16 字元集的支援，所以 Oracle 8i 用戶端無法讀取它。  
  
### <a name="working-with-utf-8-data"></a>使用 UTF-8 資料  
 若要設定替代的字元集，請將登錄機碼 HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG 設為 UTF8。 如需詳細資訊，請參閱平台上的 Oracle 安裝注意事項。 預設值是您安裝 Oracle 用戶端軟體所使用之語言的主要字元集。 如果未將語言設為與您所連接之資料庫的國家語言字元集相符，則會導致參數及資料行繫結在主要資料庫字元集中而不是在國家字元集中傳送或接收資料。  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob 僅能更新完整的字元。  
 基於可用性的理由， <xref:System.Data.OracleClient.OracleLob>物件會繼承自 .NET Framework Stream 類別，並提供**ReadByte**和**WriteByte**方法。 它也會實作用於 Oracle **LOB**物件區段的方法，例如**CopyTo**和**Erase**。 相反地，Oracle 用戶端軟體會提供一些 Api 來使用字元**LOB**s （**CLOB**和**NCLOB**）。 但是，這些 API 僅適用於完整字元。 因為這項差異，所以 Oracle 的 Data Provider 會以位元組取向的方式來執行**讀取**和**ReadByte**的支援，以處理 utf-16 資料。 不過， **OracleLob**物件的其他方法僅允許完整字元作業。  
  
## <a name="see-also"></a>另請參閱

- [Oracle 和 ADO.NET](oracle-and-adonet.md)
- [ADO.NET 概觀](ado-net-overview.md)
