---
title: "衍生自 WebResponse"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3f732f60afeba71d26391ba5fb6484ab7562654a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="deriving-from-webresponse"></a>衍生自 WebResponse
<xref:System.Net.WebResponse> 類別是抽象的基底類別，提供基本的方法和屬性以建立有特定通訊協定回應，符合 .NET Framework 插入式通訊協定模型的處理常式。 使用 <xref:System.Net.WebRequest> 類別向資源要求資料的應用程式，會收到 **WebResponse** 的回應。 通訊協定特定的 **WebResponse** 子代必須實作 **WebResponse** 類別的抽象成員。  
  
 相關聯的 **WebRequest** 類別必須建立 **WebResponse** 子代。 例如，只有呼叫 <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> 或 <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType> 才會建立 <xref:System.Net.HttpWebResponse> 執行個體。 每個 **WebResponse** 都包含向資源提出要求的結果，而且不能重複使用。  
  
## <a name="contentlength-property"></a>ContentLength 屬性  
 <xref:System.Net.WebResponse.ContentLength%2A> 屬性指出從 <xref:System.Net.WebResponse.GetResponseStream%2A> 方法傳回的資料流中可取得的資料位元組數目。 **ContentLength** 屬性不會指出伺服器所傳回的標頭或中繼資料資訊的位元組數目，它只會指出所要求資源本身的資料位元組數目。  
  
## <a name="contenttype-property"></a>ContentType 屬性  
 <xref:System.Net.WebResponse.ContentType%2A> 屬性會提供您的通訊協定要求您傳送至用戶端的任何特殊資訊，以識別伺服器要傳送的內容類型。 這通常是任何傳回資料的 MIME 內容類型。  
  
## <a name="headers-property"></a>Headers 屬性  
 <xref:System.Net.WebResponse.Headers%2A> 屬性包含與回應建立關聯的中繼資料名稱/值組任意集合。 **Headers** 屬性可以包含可表示為名稱/值組的通訊協定所需要的任何中繼資料。  
  
 您不需要使用 **Headers** 屬性，也能使用標頭中繼資料。 通訊協定特定的中繼資料可以公開為屬性。例如，<xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> 屬性會公開 **Last-Modified** HTTP 標頭。 當您將標頭中繼資料公開為屬性時，您不應該允許使用 **Headers** 屬性設定相同的屬性。  
  
## <a name="responseuri-property"></a>ResponseUri 屬性  
 <xref:System.Net.WebResponse.ResponseUri%2A> 屬性包含實際提供回應的資源 URI。 至於不支援重新導向的通訊協定，**ResponseUri** 會和建立回應的 **WebRequest** 的 <xref:System.Net.WebRequest.RequestUri%2A> 屬性相同。 如果通訊協定支援重新導向要求，**ResponseUri** 會包含回應的 URI。  
  
## <a name="close-method"></a>Close 方法  
 <xref:System.Net.WebResponse.Close%2A> 方法關閉要求和回應所建立的任何連線，並清除回應所使用的資源。 **Close** 方法會關閉回應所使用的任何資料流執行個體，但如果 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 方法的呼叫之前已關閉回應資料流，它不會擲回例外狀況。  
  
## <a name="getresponsestream-method"></a>GetResponseStream 方法  
 <xref:System.Net.WebResponse.GetResponseStream%2A> 方法傳回的資料流會包含來自所要求資源的回應。 回應資料流只包含資源傳回的資料，回應中包含的任何標頭或中繼資料都應從回應中移除，並透過通訊協定特有的屬性或 **Headers** 屬性向應用程式公開。  
  
 **GetResponseStream** 方法所傳回的資料流執行個體為應用程式所擁有，而且不用關閉 **WebResponse** 即可關閉。 依照慣例，呼叫 **WebResponse.Close** 方法也會關閉 **GetResponse** 傳回的資料流。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Net.WebResponse>  
 <xref:System.Net.HttpWebResponse>  
 <xref:System.Net.FileWebResponse>  
 [可插式通訊協定程式設計](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 [衍生自 WebRequest](../../../docs/framework/network-programming/deriving-from-webrequest.md)
