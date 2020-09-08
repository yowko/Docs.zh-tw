---
title: LINQ to XML 安全性-LINQ to XML
description: 瞭解 LINQ to XML 安全性問題，以及減輕安全性風險的方法。
ms.date: 07/20/2015
ms.assetid: ef2c0dc9-ecf9-4c17-b24e-144184ab725f
ms.openlocfilehash: 72dd2bfe2a3f0edb69645daf4625ba24fb56732b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552231"
---
# <a name="linq-to-xml-security"></a>LINQ to XML 安全性

本文說明與 LINQ to XML 相關聯的安全性問題，並提供可減輕安全性風險的指引。

## <a name="linq-to-xml-security-overview"></a>LINQ to XML 安全性總覽

與伺服器端應用程式嚴苛的安全性需求相較，LINQ to XML 的設計偏重於程式設計的便利性。 大部分 XML 案例包含處理受信任的 XML 文件，而不包含處理已上載至伺服器之不受信任的 XML 文件。 LINQ to XML 最適合這些案例。

如果您必須從未知的來源處理不受信任的資料，Microsoft 建議您使用 <xref:System.Xml.XmlReader> 類別的執行個體，該類別已設定為篩選掉已知的 XML 阻絕服務 (DoS) 攻擊。

如果您已將設定 <xref:System.Xml.XmlReader> 為緩和阻絕服務攻擊，您可以使用該讀取器來擴展 LINQ to XML 樹狀結構，但仍可受益于 LINQ to XML 的程式設計師生產力增強功能。 多數防護技術包括建立設定為減少安全性問題的讀取器，然後透過已設定的讀取器具現化 XML 樹狀結構。

XML 在本質上容易遭到阻絕服務攻擊，因為文件的大小、深度、項目名稱大小等等沒有受到限制。 不論您使用什麼元件處理 XML，如果該元件使用過多的資源，您務必要做好循環使用應用程式網域的準備。

## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>降低 XML、XSD、XPath 和 XSLT 攻擊的風險

LINQ to XML 是根據 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 建置。 LINQ to XML 透過 <xref:System.Xml.Schema?displayProperty=nameWithType> 和 <xref:System.Xml.XPath?displayProperty=nameWithType> 命名空間中的擴充方法，支援 XSD 和 XPath。 藉由使用 <xref:System.Xml.XmlReader> 、 <xref:System.Xml.XPath.XPathNavigator> 和 <xref:System.Xml.XmlWriter> 類別搭配 LINQ to XML，您就可以叫用 XSLT 來轉換 XML 樹狀結構。

如果您是在較不安全的環境中作業，則會有許多與 XML 相關聯的安全性問題，以及如何在 <xref:System.Xml?displayProperty=nameWithType> 、、和中使用類別 <xref:System.Xml.Schema?displayProperty=nameWithType> <xref:System.Xml.XPath?displayProperty=nameWithType> <xref:System.Xml.Xsl?displayProperty=nameWithType> 。 這些問題包括（但不限於）下列各項：

- XSD、XPath 和 XSLT 是以字串為基礎的語言，您在其中指定的作業可能會耗用大量的時間與金錢。 從不受信任的來源取得 XSD、XPath 或 XSLT 字串的應用程式程式設計人員必須負責驗證字串不是惡意的，或是監視並減輕評估這些字串的可能性，將會導致系統資源耗用量過高。
- XSD 架構 (包括內嵌架構) 在本質上容易遭到阻絕服務攻擊;您不應接受來自不受信任來源的架構。
- XSD 和 XSLT 可能包含其他檔案的參考，而且這類的參考可能會導致跨區域和跨網域的攻擊。
- DTD 中的外部實體可能導致跨區域和跨網域的攻擊。
- DTD 容易遭到阻絕服務攻擊。
- 特別深的 XML 文件可能會提出阻絕服務問題；您可能想要限制 XML 文件的深度。
- 請勿接受來自未受信任元件的支援元件，例如 <xref:System.Xml.NameTable> 、 <xref:System.Xml.XmlNamespaceManager> 和 <xref:System.Xml.XmlResolver> 物件。
- 讀取區塊中的資料以減少大型文件的攻擊。
- XSLT 樣式表中的指令碼區塊可能會暴露多個攻擊。
- 建構動態 XPath 運算式前，請仔細驗證。

## <a name="linq-to-xml-security-issues"></a>LINQ to XML 安全性問題

本文中的安全性問題不會以任何特定順序呈現。 所有問題都同等重要，而且應該妥善處理。

成功的權限提高攻擊可讓惡意組件更能掌控其環境。 成功的權限提高攻擊可能會導致資料洩漏、阻絕服務等等。

應用程式不應該將資料洩漏給未經授權查看該資料的使用者。

阻絕服務攻擊會使 XML 剖析器 (Parser) 或 LINQ to XML 消耗過多的記憶體或 CPU 時間。 相較於權限提高攻擊或洩漏資料攻擊，阻絕服務攻擊被視為較不嚴重。 不過，在伺服器需要處理來自不受信任來源的 XML 檔的情況下，它們很重要。

### <a name="dont-expose-error-messages-to-untrusted-callers"></a>不要將錯誤訊息公開給不受信任的呼叫者

錯誤的描述可能會顯示資料，例如，要轉換的資料、檔案名稱或實作詳細資料。 錯誤訊息不應該公開給不受信任的呼叫端。 您應該取得所有錯誤，並利用您自己自訂的錯誤訊息報告錯誤。

### <a name="dont-call-codeaccesspermissionsassert-in-an-event-handler"></a>請勿在事件處理常式中呼叫 CodeAccessPermissions

組件的權限可大可小。 權限較大的組件對電腦及其環境有較大的掌控能力。

如果權限較大之組件中的程式碼在事件處理常式中呼叫 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType>，然後將 XML 樹狀結構傳遞到具有限制權限的惡意組件，惡意組件可能會引發事件。 因為事件會以較高的許可權執行元件中的程式碼，所以惡意元件會以較高的許可權來操作。

Microsoft 建議您絕對不要在事件處理常式中呼叫 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType>。

### <a name="dont-accept-dtds-from-untrusted-sources"></a>不接受來自不受信任來源的 Dtd

DTD 中的實體本質上就不安全。 包含 DTD 的惡意 XML 檔可能會導致剖析器使用所有記憶體和 CPU 時間，進而導致阻絕服務攻擊。 因此，在 LINQ to XML 中，預設會關閉 DTD 處理。 您不應接受來自不受信任來源的 Dtd。

從不受信任來源接受 DTD 的其中一個範例為 Web 應用程式，它可讓 Web 使用者上載參考 DTD 和 DTD 檔案的 XML 檔案。 檔案經過驗證後，惡意的 DTD 就可以在您的伺服器上執行阻絕服務攻擊。 從不受信任來源接受 FTP 的另一個範例為參考網路共用上也允許匿名 FTP 存取的 DTD。

### <a name="avoid-excessive-buffer-allocation"></a>避免過度的緩衝區配置

應用程式開發人員應該知道，過大的資料來源可能會導致資源耗盡與阻絕服務攻擊。

如果惡意使用者提交或上載非常大的 XML 文件，可能會使 LINQ to XML 消耗過度的系統資源。 這可能會造成阻絕服務攻擊。 若要避免這種情況，您可以設定 <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> 屬性，然後建立可載入的檔案大小限制的讀取器。 然後，您可以使用讀取器建立 XML 樹狀結構。

例如，如果您知道來自不受信任來源的 XML 文件預期大小上限將小於 50K 位元組，將 <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> 設定為 100,000。 這將不會妨礙您處理 XML 文件，同時，這會降低文件上載時，消耗大量記憶體的阻絕服務威脅。

### <a name="avoid-excess-entity-expansion"></a>避免過度的實體展開

使用 DTD 時，其中一個已知的阻絕服務攻擊為造成實體過度擴充的文件。 若要避免這種情況，您可以設定 <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> 屬性，然後建立讀取器，然後限制實體展開所產生的字元數。 然後，您可以使用讀取器建立 XML 樹狀結構。

### <a name="limit-the-depth-of-the-xml-hierarchy"></a>限制 XML 階層的深度

其中一個可能的阻絕服務攻擊會發生在提交階層過深的文件時。 若要避免這種情況，您可以 <xref:System.Xml.XmlReader> 在自己的類別中包裝，以計算專案的深度。 如果深度超過預先決定的合理層級，您可以中止惡意文件的處理。

### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>防止未受信任的 XmlReader 或 XmlWriter 執行

管理員應該確認外部提供的任何 <xref:System.Xml.XmlReader> 或 <xref:System.Xml.XmlWriter> 實作具有強式名稱，而且已經在電腦組態中註冊。 這樣可以防止惡意程式碼偽裝成讀取器或寫入器進行載入。

### <a name="periodically-free-objects-that-reference-xname"></a>定期釋放參考 XName 的物件

為防止特定種類的攻擊，應用程式設計人員應該在應用程式網域中，定期釋放參考 <xref:System.Xml.Linq.XName> 物件的所有物件。

### <a name="protect-against-random-xml-names"></a>防止隨機 XML 名稱

從不受信任來源取得資料的應用程式，應該考慮使用 <xref:System.Xml.XmlReader> 包裝在自訂程式碼中的來檢查是否有隨機 XML 名稱和命名空間的可能性。 如果偵測到這類的 XML 隨機名稱與命名空間，應用程式可以中止惡意文件的處理。

您可能想要在任何指定的命名空間 (包括沒有命名空間中的名稱) 中，將名稱數限制為合理的限制。

### <a name="serialize-linq-to-xml-objects-to-xml-text-before-passing-the-data-to-an-untrusted-component"></a>將 LINQ to XML 物件序列化為 XML 文字，然後將資料傳遞至不受信任的元件

LINQ to XML 可以用來建立處理管線，讓不同的應用程式元件載入、驗證、查詢、轉換、更新和儲存在元件之間傳遞的 xml 資料做為 XML 樹狀結構。 由於將物件載入並序列化為 XML 文字的負荷僅能在管線尾端完成，因此這可能有助於將效能最佳化。 不過，開發人員必須知道透過一個元件所建立的所有附註和事件處理常式都可以存取其他元件。 如果這些元件有不同程度的信任，這可能會產生數個弱點。 若要透過較不受信任的元件建置安全的管線，您必須先將 LINQ to XML 物件序列化為 XML 文字，然後再將資料傳遞到不受信任的元件。

有些安全性是由 Common Language Runtime (CLR) 提供。 例如，不包含私用類別的元件無法存取該類別所索引的注釋。 不過，批註可以由無法讀取的元件來刪除。 這可以當做竄改攻擊使用。

## <a name="see-also"></a>另請參閱

- [LINQ to XML 總覽](linq-xml-overview.md)
