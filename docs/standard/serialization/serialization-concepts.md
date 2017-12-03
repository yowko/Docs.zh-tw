---
title: "序列化概念"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1f442f450aea5833fd21e57980c842cc1559ccc1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="serialization-concepts"></a>序列化概念
為何會想要使用序列化？ 最重要的兩大原因是，在儲存媒體中保持物件的狀態以便在稍後階段重建完全相同的複本，以及利用值在應用程式定義域之間傳送物件。 例如，使用序列化來儲存 ASP.NET 的工作階段狀態，並且複製物件至 Windows Forms 的剪貼簿。 它也供遠端使用，利用值在應用程式定義域之間傳遞物件。

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>持續性儲存體
經常有需要將物件的欄位值儲存至磁碟，稍後再擷取此資料的情況。 儘管不需序列化就可以輕易取得，但是此做法經常繁瑣而易出錯，而且當需要追蹤物件階層時會變得越來越複雜。 想像撰寫包含數千個物件的大型企業應用程式，且必須對所有物件撰寫程式碼，將欄位和屬性儲存至磁碟和從磁碟中還原。 序列化提供方便的機制達到此目的。

Common Language Runtime 管理物件在記憶體中儲存的方式，並使用[反映](../../../docs/framework/reflection-and-codedom/reflection.md)提供自動的序列化機制。 當物件序列化後，類別名稱、組件以及類別執行個體的所有資料成員都會寫入儲存區。 物件通常將對其他執行個體的參考儲存在成員變數中。 將類別序列化後，序列化引擎會追蹤已序列化的參考物件，確保不會將相同的物件序列化多次。 隨 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]所提供的序列化架構會正確地自動處理物件圖形和循環參考。 對物件圖形的唯一要求是所有由已序列化物件所參考的物件，必須也標示為 `Serializable` (如需詳細資訊，請參閱[基本序列化](basic-serialization.md))。 若不這麼做，當序列化程式嘗試序列化未標示的物件時，將擲回例外狀況。

將已序列化的類別還原序列化時，會重新建立該類別且自動還原所有資料成員的值。

## <a name="marshal-by-value"></a>以傳值方式封送處理
物件只有在建立它們的應用程式定義域中才有效。 除非物件衍生自 `MarshalByRefObject` 或是標示為 `Serializable`，否則任何嘗試將物件當作參數傳遞，或將物件當作結果傳回的做法都將失敗。 如果物件標示為 `Serializable`，則會自動序列化該物件，並從某個應用程式定義域傳輸至其他定義域，然後在第二個應用程式定義域中還原序列化以產生完全相同的物件複本。 此程序一般稱為傳值封送處理。
 
物件衍生自 `MarshalByRefObject` 時，會將物件參考從某個應用程式定義域傳遞到另一個定義域，而不是物件本身。 您也可以將衍生自 `MarshalByRefObject` 的物件標示為 `Serializable`。 以遠端處理使用此物件時，已由代理選取器 (`SurrogateSelector`) 預先設定並負責序列化的格式子，並控制序列化處理序，然後取代所有具有 Proxy 且衍生自 `MarshalByRefObject` 的物件。 如果沒有 `SurrogateSelector`，序列化架構會遵循在[序列化程序中的步驟](steps-in-the-serialization-process.md)中說明的標準序列化規則。  

## <a name="related-sections"></a>相關章節  
 [二進位序列化](../../../docs/standard/serialization/binary-serialization.md)  
 說明 Common Language Runtime 中所含的二進位序列化機制。  
  
 [遠端物件](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58)  
 說明 .NET Framework 中可用來進行遠端通訊的各種通訊方法。  
  
 [XML 和 SOAP 序列化](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 說明 Common Language Runtime 中所含的 XML 和 SOAP 序列化機制。
