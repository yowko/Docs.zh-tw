---
title: XML 序列化程式產生器工具 (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: bc1a0abaeef9a9244aa83941e590063c7ef167d1
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588368"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a>XML 序列化程式產生器工具 (Sgen.exe)

XML 序列化器產生器為指定程式集中的類型創建 XML 序列化程式集。 序列化程式集在序列化或取消序列化<xref:System.Xml.Serialization.XmlSerializer>指定類型的物件時提高了 啟動性能。
  
## <a name="syntax"></a>語法

從命令行運行該工具。
  
```console  
sgen [options]  
```
  
> [!TIP]
> 對於 .NET 框架工具要正常運行,必須`Path``Include`正確`Lib`設置、和環境變數。 執行位於 \<SDK>\v2.0\Bin 目錄中的 SDKVars.bat，即可設定這些環境變數。 SDKVars.bat 必須在每一個命令提示字元中執行。
  
## <a name="parameters"></a>參數  
  
|選項|描述|  
|------------|-----------------|  
|**/ssembly\[\]:**_檔案名稱_|為組件中包含的所有類型或 *filename* 所指定的可執行檔產生序列化程式碼。 只能提供一個檔名。 如果重複使用這個引數，則會使用最後一個檔名。|  
|**/c\[歐\]皮 勒 :**_選項_|指定要傳遞至 C# 編譯器的選項。 所有 csc.exe 選項都受到支援，可以傳遞至編譯器。 這個選項可以用來指定組件必須經過簽署，並指定金鑰檔。|  
|**/d\[ebug\]**|產生可以與偵錯工具搭配使用的影像。|  
|**/f\[奧爾塞\]**|強制覆寫現有的同名組件。 預設值為**false**。|  
|**/help 或 /?**|顯示工具的命令語法和選項。|  
|**/k\[eep\]**|將產生的原始程式檔 (Source File) 和其他暫存檔案編譯成序列化組件之後，隱藏刪除這些檔案的動作。 這個選項可以用來判斷工具是否正在為特定的型別產生序列化程式碼。|  
|**/n\[奧洛戈\]**|隱藏顯示 Microsoft 程式啟始資訊。|  
|**/o\[\]ut :**_路徑_|指定要在其中儲存所產生之組件的目錄。 **注意：** 產生的組件名稱是由輸入組件的名稱加上 "xmlSerializers.dll" 所組成。|  
|**/p\[羅西型\]**|只為 XML Web 服務 Proxy 型別產生序列化程式碼。|  
|**/r\[efers\]:**_程式集檔案_|指定要求 XML 序列化的型別所參考的組件。 這個選項接受以逗號分隔多個組件檔案。|  
|**/s\[ilent\]**|隱藏顯示成功訊息。|  
|**/t\[\]ype :**_類型_|只為指定的型別產生序列化程式碼。|  
|**/v\[erbose\]**|顯示詳細資訊輸出以供偵錯。 此選項會列出無法使用 <xref:System.Xml.Serialization.XmlSerializer> 進行序列化之目標組件中的型別。|  
|**/?**|顯示工具的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
 如果未使用 XML 序列化程式產生器，則每當應用程式執行時，<xref:System.Xml.Serialization.XmlSerializer> 便會為每個型別產生序列化程式碼和序列化組件。 為了提高 XML 序列化啟動的性能,請使用 Sgen.exe 工具提前生成這些程式集。 然後，這些組件便可以與應用程式一起部署。  
  
 XML 序列化程式產生器也可以改善用戶端使用 XML Web Service Proxy 與伺服器進行通訊的效能，因為在第一次載入型別時，序列化處理序並不會影響到效能。  
  
 這些產生的組件無法在 Web 服務的伺服器端上使用。 這個工具只能在 Web 服務用戶端和手動序列化案例中使用。  
  
 如果含有要序列化之型別的組件名稱為 MyType.dll，關聯的序列化組件名稱就會是 MyType.XmlSerializers.dll。  
  
## <a name="examples"></a>範例  
 下列命令會建立名為 Data.XmlSerializers.dll 的組件，用以序列化 Data.dll 組件中所包含的所有型別。  
  
```console  
sgen Data.dll
```  
  
 Data.XmlSerializers.dll 組件可以從程式碼參考，而該程式碼必須序列化及還原序列化 Data.dll 中的型別。  
  
## <a name="see-also"></a>另請參閱

- [工具](../../../docs/framework/tools/index.md)
- [指令提示](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
