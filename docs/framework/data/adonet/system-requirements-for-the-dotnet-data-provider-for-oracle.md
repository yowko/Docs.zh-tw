---
title: ".NET Framework Data Provider for Oracle 的系統需求 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# .NET Framework Data Provider for Oracle 的系統需求
Oracle 的 .NET Framework 資料提供者需要 Microsoft Data Access Components \(MDAC\) 2.6 \(含\) 以後版本。  建議使用 MDAC 2.8 SP1。  
  
 您也必須安裝 Oracle 8i 第 3 版 \(8.1.7\) 用戶端 \(含\) 以後版本。  
  
 Oracle 9i 版之前的 Oracle 用戶端軟體無法存取 UTF16 資料庫，因為 UTF16 是 Oracle 9i 的新功能。  若要使用此功能，您必須將用戶端軟體升級至 Oracle 9i \(含\) 以後版本。  
  
## 使用 Oracle 及 Unicode 資料的資料提供者  
 當您在使用 Oracle 的 .NET Framework 資料提供者及 Oracle 用戶端程式庫時，應該考量下列的 Unicode 相關問題清單。  如需詳細資訊，請參閱 Oracle 文件。  
  
### 設定連接字串屬性中的 Unicode 值  
 使用 Oracle 時，您可以使用連接字串屬性  
  
```  
Unicode=True   
```  
  
 以 UTF\-16 模式初始化 Oracle 用戶端程式庫。  這會導致 Oracle 用戶端程式庫接受 UTF\-16 \(與 UCS\-2 非常類似\)，而不接受多位元組的字串。  這可讓 Oracle 的資料提供者一律使用 Oracle 字碼頁，而無需進行其他轉譯工作。  僅在您使用 Oracle 9i 用戶端與具有 AL16UTF16 替代字元集的 Oracle 9i 資料庫通訊時，此組態才會運作。  當 Oracle 9i 用戶端與 Oracle 9i 伺服器通訊時，需要使用其他資源將 Unicode **CommandText** 值轉換成 Oracle9i 伺服器所使用之適當的多位元組字元集。  如果您知道將 `Unicode=True` 加入連接字串會得到安全的組態，便可避免此問題。  
  
### Oracle 用戶端及 Oracle 伺服器的混合版本  
 當伺服器的國家字元集指定為 AL16UTF16 \(Oracle 9i 的預設值\) 時，Oracle 8i 用戶端無法存取 Oracle 9i 資料庫中的 **NCHAR**、**NVARCHAR2** 或 **NCLOB** 資料。  因為 Oracle 9i 之前的版本未引入對 UTF\-16 字元集的支援，所以 Oracle 8i 用戶端無法讀取它。  
  
### 使用 UTF\-8 資料  
 若要設定替代的字元集，請將登錄機碼 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\ORACLE\\HOMEID\\NLS\_LANG 設為 UTF8。  如需詳細資訊，請參閱平台上的 Oracle 安裝注意事項。  預設值是您安裝 Oracle 用戶端軟體所使用之語言的主要字元集。  如果未將語言設為與您所連接之資料庫的國家語言字元集相符，則會導致參數及資料行繫結在主要資料庫字元集中而不是在國家字元集中傳送或接收資料。  
  
### OracleLob 僅能更新完整的字元。  
 由於可用性的原因，<xref:System.Data.OracleClient.OracleLob> 物件會繼承自 .NET Framework Stream 類別 \(Class\)，並提供 **ReadByte** 及 **WriteByte** 方法。  它也實作適用於 Oracle **LOB** 物件之區段的方法，如 **CopyTo** 及 **Erase**。  相反地，Oracle 用戶端軟體會提供許多 API，以使用字元 **LOB** \(**CLOB** 及 **NCLOB**\)。  但是，這些 API 僅適用於完整字元。  由於此差別，Oracle 的資料提供者會實作 **Read** 及 **ReadByte** 的支援，以位元組方式使用 UTF\-16 資料。  但是，**OracleLob** 物件的其他方法僅允許完整字元作業。  
  
## 請參閱  
 [Oracle 和 ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)