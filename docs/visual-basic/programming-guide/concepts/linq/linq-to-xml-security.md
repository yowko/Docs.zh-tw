---
title: LINQ to XML 安全性 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d99b4af2-d447-4a3b-991b-6da0231a8637
ms.openlocfilehash: 3f75377502b30b03090bb2a5fe720faf4e12a028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-security-visual-basic"></a>LINQ to XML 安全性 (Visual Basic)
這個主題描述與 LINQ to XML 相關聯的安全性問題。 此外，還提供減少暴露安全性的部分指引。  
  
## <a name="linq-to-xml-security-overview"></a>LINQ to XML 安全性概觀  
 與伺服器端應用程式嚴苛的安全性需求相較，LINQ to XML 的設計偏重於程式設計的便利性。 大部分 XML 案例包含處理受信任的 XML 文件，而不包含處理已上載至伺服器之不受信任的 XML 文件。 LINQ to XML 最適合這些案例。  
  
 如果您必須從未知的來源處理不受信任的資料，Microsoft 建議您使用 <xref:System.Xml.XmlReader> 類別的執行個體，該類別已設定為篩選掉已知的 XML 阻絕服務 (DoS) 攻擊。  
  
 如果您已經將 <xref:System.Xml.XmlReader> 設定為減少阻絕服務攻擊，您可以使用該讀取器填入 LINQ to XML 樹狀結構，而且仍然可以享受 LINQ to XML 的程式設計師產能加強功能。 多數防護技術包括建立設定為減少安全性問題的讀取器，然後透過已設定的讀取器具現化 XML 樹狀結構。  
  
 XML 在本質上容易遭到阻絕服務攻擊，因為文件的大小、深度、項目名稱大小等等沒有受到限制。 不論您使用什麼元件處理 XML，如果該元件使用過多的資源，您務必要做好循環使用應用程式網域的準備。  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>減少 XML、XSD、XPath 和 XSLT 攻擊  
 LINQ to XML 是根據 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlWriter> 建置。 LINQ to XML 透過 <xref:System.Xml.Schema?displayProperty=nameWithType> 和 <xref:System.Xml.XPath?displayProperty=nameWithType> 命名空間中的擴充方法，支援 XSD 和 XPath。 使用 <xref:System.Xml.XmlReader>、<xref:System.Xml.XPath.XPathNavigator> 和 <xref:System.Xml.XmlWriter> 類別搭配 LINQ to XML 時，您可以叫用 XSLT 來轉換 XML 樹狀結構。  
  
 如果您要在較不安全的環境下操作，則會有一些與 XML 相關聯的安全性問題，以及在 <xref:System.Xml?displayProperty=nameWithType>、<xref:System.Xml.Schema?displayProperty=nameWithType>、<xref:System.Xml.XPath?displayProperty=nameWithType> 和 <xref:System.Xml.Xsl?displayProperty=nameWithType> 中使用類別的安全性問題。 這些包括 (但不限於) 下列問題：  
  
-   XSD、XPath 和 XSLT 是以字串為基礎的語言，您在其中指定的作業可能會耗用大量的時間與金錢。 從不受信任的來源取出 XSD、XPath 或 XSLT 字串的應用程式設計人員要負責驗證這些不是惡意的字串，或監視與降低評估這些字串將導致過度耗用系統資源的可能性。  
  
-   XSD 結構描述 (包括內嵌結構描述) 在本質上容易遭到阻絕服務攻擊；您不應接受來自不受支援之來源的結構描述。  
  
-   XSD 和 XSLT 可能包含其他檔案的參考，而且這類的參考可能會導致跨區域和跨網域的攻擊。  
  
-   DTD 中的外部實體可能導致跨區域和跨網域的攻擊。  
  
-   DTD 容易遭到阻絕服務攻擊。  
  
-   特別深的 XML 文件可能會提出阻絕服務問題；您可能想要限制 XML 文件的深度。  
  
-   請勿接受來自不受信任組件的支援元件，例如，<xref:System.Xml.NameTable>、<xref:System.Xml.XmlNamespaceManager> 和 <xref:System.Xml.XmlResolver> 物件。  
  
-   讀取區塊中的資料以減少大型文件的攻擊。  
  
-   XSLT 樣式表中的指令碼區塊可能會暴露多個攻擊。  
  
-   建構動態 XPath 運算式前，請仔細驗證。  
  
## <a name="linq-to-xml-security-issues"></a>LINQ to XML 安全性問題  
 本主題中的安全性問題不會以特定的順序呈現。 所有問題都同等重要，而且應該妥善處理。  
  
 成功的權限提高攻擊可讓惡意組件更能掌控其環境。 成功的權限提高攻擊可能會導致資料洩漏、阻絕服務等等。  
  
 應用程式不應將資料洩漏給沒有查看該資料之權限的使用者。  
  
 阻絕服務攻擊會使 XML 剖析器 (Parser) 或 LINQ to XML 消耗過多的記憶體或 CPU 時間。 相較於權限提高攻擊或洩漏資料攻擊，阻絕服務攻擊被視為較不嚴重。 不過，如果是在伺服器需要處理來自不受信任來源之 XML 文件的情況下，阻絕服務攻擊就很重要。  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>例外情形與錯誤訊息可能會顯示資料  
 錯誤的描述可能會顯示資料，例如，要轉換的資料、檔案名稱或實作詳細資料。 錯誤訊息不得公開給不受信任的呼叫端。 您應該取得所有錯誤，並利用您自己自訂的錯誤訊息報告錯誤。  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>請勿在事件處理常式中呼叫 CodeAccessPermissions.Assert  
 組件的權限可大可小。 權限較大的組件對電腦及其環境有較大的掌控能力。  
  
 如果權限較大之組件中的程式碼在事件處理常式中呼叫 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType>，然後將 XML 樹狀結構傳遞到具有限制權限的惡意組件，惡意組件可能會引發事件。 由於事件會在權限較大的組件中執行程式碼，因此惡意組件會以更高的權限操作。  
  
 Microsoft 建議您絕對不要在事件處理常式中呼叫 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType>。  
  
### <a name="dtds-are-not-secure"></a>DTD 不安全  
 DTD 中的實體本質上就不安全。 包含 DTD 的惡意 XML 文件可能會讓剖析器用掉所有記憶體和 CPU 時間，造成阻絕服務攻擊。 因此，在 LINQ to XML 中，預設會關閉 DTD 處理。 您不應該接受來自不受信任來源的 DTD。  
  
 從不受信任來源接受 DTD 的其中一個範例為 Web 應用程式，它可讓 Web 使用者上載參考 DTD 和 DTD 檔案的 XML 檔案。 檔案經過驗證後，惡意的 DTD 就可以在您的伺服器上執行阻絕服務攻擊。 從不受信任來源接受 FTP 的另一個範例為參考網路共用上也允許匿名 FTP 存取的 DTD。  
  
### <a name="avoid-excessive-buffer-allocation"></a>避免配置過度的緩衝區  
 應用程式開發人員應該知道，過大的資料來源可能會導致資源耗盡與阻絕服務攻擊。  
  
 如果惡意使用者提交或上載非常大的 XML 文件，可能會使 LINQ to XML 消耗過度的系統資源。 這可能會造成阻絕服務攻擊。 為防止這個情況，您可以設定 <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> 屬性，並建立限制載入文件之大小的讀取器。 然後，您可以使用讀取器建立 XML 樹狀結構。  
  
 例如，如果您知道來自不受信任來源的 XML 文件預期大小上限將小於 50K 位元組，將 <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> 設定為 100,000。 這將不會妨礙您處理 XML 文件，同時，這會降低文件上載時，消耗大量記憶體的阻絕服務威脅。  
  
### <a name="avoid-excess-entity-expansion"></a>避免過度擴充實體  
 使用 DTD 時，其中一個已知的阻絕服務攻擊為造成實體過度擴充的文件。 為防止這個情況，您可以設定 <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> 屬性，並建立限制實體擴充產生之字元數的讀取器。 然後，您可以使用讀取器建立 XML 樹狀結構。  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>限制 XML 階層的深度  
 其中一個可能的阻絕服務攻擊會發生在提交階層過深的文件時。 為防止這個情況，您可以利用自己的類別，包裝計算項目深度的 <xref:System.Xml.XmlReader>。 如果深度超過預先決定的合理層級，您可以中止惡意文件的處理。  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>防止不受信任的 XmlReader 或 XmlWriter 實作  
 管理員應該確認外部提供的任何 <xref:System.Xml.XmlReader> 或 <xref:System.Xml.XmlWriter> 實作具有強式名稱，而且已經在電腦組態中註冊。 這樣可以防止惡意程式碼偽裝成讀取器或寫入器進行載入。  
  
### <a name="periodically-free-objects-that-reference-xname"></a>定期釋放參考 Xname 的物件  
 為防止特定種類的攻擊，應用程式設計人員應該在應用程式網域中，定期釋放參考 <xref:System.Xml.Linq.XName> 物件的所有物件。  
  
### <a name="protect-against-random-xml-names"></a>防止 XML 隨機名稱  
 從未受信任來源取出資料的應用程式應該考慮使用以自訂程式碼包裝的 <xref:System.Xml.XmlReader> 來檢查 XML 隨機名稱與命名空間的可能性。 如果偵測到這類的 XML 隨機名稱與命名空間，應用程式可以中止惡意文件的處理。  
  
 您可能想要在任何指定的命名空間 (包括沒有命名空間中的名稱) 中，將名稱數限制為合理的限制。  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>附註可由共用 LINQ to XML 樹狀結構的軟體元件存取  
 LINQ to XML 可用於建置處理管線，其中的不同應用程式元件可以載入、驗證、查詢、轉換、更新與儲存在元件之間當做 XML 樹狀結構傳遞的 XML 資料。 由於將物件載入並序列化為 XML 文字的負荷僅能在管線尾端完成，因此這可能有助於將效能最佳化。 不過，開發人員必須知道透過一個元件所建立的所有附註和事件處理常式都可以存取其他元件。 如果這些元件有不同程度的信任，這可能會產生數個弱點。 若要透過較不受信任的元件建置安全的管線，您必須先將 LINQ to XML 物件序列化為 XML 文字，然後再將資料傳遞到不受信任的元件。  
  
 有些安全性是由 Common Language Runtime (CLR) 提供。 例如，不包含私用類別的元件無法存取透過該類別輸入的附註。 不過，無法讀取附註的元件可以刪除這些附註。 這可以當做竄改攻擊使用。  
  
## <a name="see-also"></a>另請參閱  
 [程式設計手冊 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
