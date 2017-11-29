---
title: "工具"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89c907f9-313f-408c-992a-631f1eadf1da
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ad963bf04cfbf057128421d0808a2f6b6a78c2bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="tools"></a>工具
本主題將列出由 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 工具所產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|ParametersTarget|\<列舉 >|  
|ParametersToolConfig|\<configFile >|  
|ErrInvalidPath|指定的路徑無效。 請檢查指定的引數。|  
|ParametersReference|\<檔案路徑 >|  
|WrnCannotLoadConfigFileForValidation|在處理從指定位置載入的組態檔時發生錯誤。 無法驗證此組態檔中定義的服務。|  
|MoreHelp|如需詳細說明，請輸入 "svcutil" 並包含指定引數。|  
|HelpMergeConfig|會導致產生的組態合併到現有的檔案，而不是覆寫現有的檔案。|  
|ErrCannotWriteFile|無法寫入輸出檔。|  
|ErrInvalidNamespaceArgument|指定的無效值已傳遞給指定的選項。 指定逗號分隔的目標命名空間與 CLR 命名空間組。|  
|HelpImportXmlType|設定 DataContract 序列化程式將非 DataContract 類型當成 IXmlSerializable 類型來匯入。|  
|ErrExclusiveOptionsSpecified|一旦指定了其他指定選項，就無法使用指定的選項。|  
|WrnHttpGetFailed|包含指定 URI 的 HTTP GET 錯誤。|  
|ErrInputFileNotAssemblyOrMetadata|透過指定輸入引數所讀取的指定位置裡的檔案，看起來不像是 XML 中繼資料檔或有效的組件。|  
|WrnUnknownMetadataFound|無法儲存無法辨識的指定類型中繼資料文件。|  
|ErrDirectoryContainsInvalidCharacters|指定的無效值已傳遞給指定的選項。 路徑不允許指定的字元。|  
|WrnCannotResolveServiceForValidation|無法載入包含指定 configName 的服務。 若要驗證服務，請同時提供包含服務類型的組件，以及包含此服務組態的可執行檔。|  
|ErrUnexpectedValue|指定的選項不支援任何值。|  
|#InvalidArg|指定項目內含無效引數。|  
|ParametersExcludeType|\<type>|  
|HelpXmlSerializer|產生資料型別，這些型別會使用 XmlSerializer 來進行序列化和還原序列化。|  
|#|---------------------------------------------------------------------------------------------------------------------=|  
|ErrUnexpectedError|工具中出現錯誤。|  
|HelpNologo|已隱藏著作權與橫幅資訊。|  
|ErrInputConflictsWithTarget|從指定項目中讀取的輸入型別不支援將指定選項設為指定值。|  
|WrnCannotLoadServiceForExport|載入要匯出的服務類型時發生錯誤。|  
|HelpMetadataDownloadCategory|-= 中繼資料下載 =-|  
|WrnNoServiceContractTypes|無法產生指定組件的 XmlSerializer 型別。 找不到服務合約類型。|  
|WrnCouldNotLoadTypesFromReferenceAssemblyAt|在載入先前從指定項目載入的組件型別時發生錯誤。 無法載入組件中某些型別，因此無法提供給工具使用。|  
|ErrDirectoryPointsToAFile|指定的無效值已傳遞給指定的選項。 指定值為檔案路徑。|  
|錯誤|錯誤：|  
|ErrDuplicateReferenceValues|已使用指定選項來載入指定組件兩次。 組件只能當作參照一次。|  
|WrnNoXmlSerializerOperationBehavior|無法產生指定組件的 XmlSerializer。 組件中的所有服務合約都未與 XmlSerializerOperationBehavior 一起運作。|  
|ErrCannotCreateDirectory|無法建立指定目錄。|  
|ErrCouldNotLoadTypesFromAssemblyAt|無法將任何型別載入指定組件中。|  
|ErrUnknownSwitch|指定的參數為無法辨識的選項。|  
|Logo|工具的標誌為包含版本資訊的 "Microsoft ® Service Model Metadata Tool"。|  
|NoCodeWasGenerated|未產生任何程式碼。<br /><br /> 如果您之前嘗試產生用戶端，可能是因為中繼資料文件並未包含任何有效的合約或服務<br /><br /> 或是因為所有合約/服務被發現存在參照組件中。 請確認您已將所有中繼資料文件傳送至工具中。|  
|WrnUnableToLoadContractForSGen|載入合約類型時發生錯誤。 無法產生此合約的 XmlSerializer 型別。 指定了型別和詳細資料。|  
|WrnOptionConflictsWithInput|無法將指定選項與多個輸入組件一起使用。 已忽略指定選項。|  
|ErrUnableToImportMetadata|嘗試匯入中繼資料時發生嚴重錯誤。|  
|ErrInvalidSerializer|無效的序列化程式已經傳送至指定選項中。 已指定支援的序列化程式。|  
|SavingDownloadedMetadata|正在儲存下載的中繼資料檔...|  
|WrnNoConfigForServices|所傳送的組件沒有一個是包含組態檔的可執行檔，或者沒有一個組態檔包含帶有指定組態名稱的服務。|  
|ErrInputConflictsWithOption|從指定項目讀取的輸入無法用來搭配指定選項，因為它們意指不同的工具作業模式。|  
|ErrUnableToExportEndpoints|匯出指定服務類型時發生錯誤。|  
|ErrInputSchemaParseError|讀取指定項目時發生 XML 結構描述剖析錯誤。 請驗證 XML 格式正確而且有效。|  
|ErrInputPolicyParseError|讀取指定項目時發生 WS-Policy 剖析錯誤。 請驗證 XML 格式正確而且有效。|  
|ErrUnableToLoadReferenceType|載入參照的合約類型時發生錯誤。 已忽略指定類型。|  
|WrnCannotLoadServiceForValidation|載入要驗證的服務時發生錯誤。 指定了型別和詳細資料。|  
|HelpCodeGenerationCategory|-= 程式碼產生 =-|  
|RetreivingMetadataWithMexAndDisco|使用 WS-Metadata Exchange 或 DISCO 嘗試從指定項目中下載中繼資料。|  
|ErrGeneralSchemaValidation|驗證在匯出期間產生的 XML 結構描述時發生錯誤。|  
|ParametersDirectory|\<目錄 >|  
|ErrCannotLoadSpecifiedType|無法針對已經傳送至指定選項的指定值載入任何型別。 請確定此型別所屬的組件係透過指定選項來指定。|  
|ErrOptionModeConflict|指定選項無法搭配指定選項一起使用，因為它們意指不同的輸出類型。|  
|ErrIsNotAnAssembly|無法將指定項目當成組件載入。 請驗證此檔案為 .NET 組件。|  
|ErrInputConflictsWithMode|從指定項目讀取的輸入與其他選項不一致。|  
|ErrDuplicateValuePassedToTypeArg|指定值已經多次傳送至指定選項。 每種型別只能指定一次。|  
|ErrInputEPRFileParseError|無法從指定項目讀取端點參照。 請驗證 XML 格式正確而且有效。|  
|ErrCouldNotCreateCodeProvider|您無法針對已經傳送至 /{1} 引數的指定值建立程式碼提供者。 請驗證程式碼提供者已安裝且設定妥當。|  
|ErrPathTooLongDirOnly|結果指定路徑太長。 請檢視指定引數。|  
|HelpDataContractSerializer|產生使用 DataContract 序列化程式以進行序列化與還原序列化的資料型別。|  
|ErrUnableToExportEndpoint|匯出指定命名空間之指定端點名稱時發生錯誤，此命名空間可在組件所載入的組態檔之指定服務型別中找到。|  
|HelpUsage1|顯示說明用法。|  
|HelpUsage2|顯示說明用法。|  
|HelpUsage3|顯示說明用法。|  
|HelpUsage4|顯示說明用法。|  
|HelpUsage5|顯示說明用法。|  
|ErrDirectoryNotFound|找不到指定目錄。 請驗證目錄確實存在，而且您具有適當的讀取權限。|  
|ErrUnableToLoadFile|無法讀取指定檔案。|  
|ErrNoFilesFound|指定的輸入路徑並未參照到任何現有檔案。|  
|ParametersConfig|\<configFile >|  
|ErrDirectoryInsteadOfFile|指定的輸入路徑可能是目錄。 輸入必須是 URL 或檔案路徑。|  
|HelpConfig|指示工具使用提供的名稱來產生組態檔。 預設：output.config。|  
|ErrSingleUseSwitch|您無法多次指定選項。|  
|警告|警告:|  
|WrnAmbiguousServiceConfig|找到包含指定組態名稱的多個服務組態，且下列組件已指定。|  
|ErrInvalidInputPath|指定的輸入路徑並未參照到任何現有檔案，而且可能不是有效的 URI。|  
|ErrUnableToLoadInputs|讀取載入的中繼資料時發生錯誤。|  
|GeneratingSerializer|正在產生 XML 序列化程式...|  
|HelpToolConfig|用來取代應用程式組態檔的自訂組態檔。 這可用於變更中繼資料組態或註冊組態副檔名，而不用更改工具的組態檔。|  
|ErrValidateInvalidUse|指定選項無法搭配使用指定選項。|  
|WrnWSMExFailed|包含指定 URI 的 WS-Metadata Exchange 錯誤。|  
|HelpNoconfig|不要產生組態。|  
|HelpCodeGenerationDescription|指定項目可從中繼資料文件產生服務合約、用戶端和資料型別。|  
|HelpTargetMetadata|輸出中繼資料。 如果輸入為 URL，則 Svcutil.exe 會將中繼資料儲存到磁碟，而且不會產生程式碼。 如果輸入為一或多個組件，則 Svcutil.exe 會從組件型別中產生中繼資料。|  
|ErrAmbiguousOptionModeConflict|指定選項與其他選項衝突。 請檢視您的工具用法。|  
|ErrNotLanguageOrCodeDomType|傳送至指定引數的指定值並未代表定義語言，因此無法當成完整的 CLR 型別來載入。|  
|ErrUnableToUniquifyFilename|無法建立輸出檔名。 有太多檔案使用指定的前置詞來建立。|  
|ErrCannotCreateFile|無法建立指定的輸出檔。|  
|ErrExpectedValue|指定選項要求指定某值。|  
|ErrCannotDisambiguateSpecifiedTypes|一個以上具有相同名稱的型別存在參照的組件集中。 請使用符合組件規格的名稱來區分指定選項的各個指定型別。|  
|RetreivingMetadataWithMexOnly|使用 WS-Metadata Exchange 嘗試從指定位置下載中繼資料。 這個 URL 不支援 DISCO。|  
|ErrInvalidTarget|使用指定項目來指定時，指定目標將失效。 已指定支援目標。|  
|ErrPathTooLong|結果路徑太長。 請檢視指定引數。|  
|HelpCommonOptionsCategory|-= 常見問題 =-|  
|ParametersServiceName|\<serviceConfigName >|  
|ErrNoValidInputFilesSpecified|未指定有效的輸入檔。 請指定中繼資料文件或組件檔。|  
|ParametersLanguage|\<語言 >|  
|ErrUnableToLoadMetadataDocument|從其中一個載入的文件讀取中繼資料時發生錯誤。 已指定文件識別項。|  
|ErrConflictingInputs|指定的輸入引數與指定項目衝突，因為它們意指不同的工具作業模式。|  
|WrnUnableToLoadContractForValidation|載入合約類型時發生錯誤。 指定了型別和詳細資料。|  
|WrnAttributeReflectionErrors|從指定項目中載入的組件中，某些型別無法執行屬性反映。 請驗證此組件可藉由適當的安全性權限從此位置載入。|  
|HelpMetadataExportCategory|-= 中繼資料匯出 =-|  
|HelpValidationCategory|-= 服務驗證 =-|  
|ValidationError|驗證錯誤：|  
|GeneratingFiles|正在產生檔案...|  
|ErrCannotSpecifyMultipleMappingsForNamespace|已將無效值傳遞給指定選項。 指定的目標命名空間無法對應至多個指定的 CLR 命名空間。|  
|ErrCouldNotLoadReferenceAssemblyAt|無法載入指定的參照組件。|  
|ParametersOut|\<檔案 >|  
|NoCodeWasGeneratedSuggestDCOnly|若要從結構描述中產生合約，請使用指定選項。|  
|ErrUnableToLoadInputConfig|無法載入指定的組態檔。|  
|ErrUnexpectedDelimiter|無效的引數分隔符號 (':' or '=') 無法啟動選項。|  
|ErrMergeConfigUsedWithoutConfig|無法在不指定其他指定選項的情況下使用指定選項。|  
|ErrUnableToExportContract|匯出從指定型別中載入的合約時發生錯誤。|  
|GeneratingMetadata|正在產生中繼資料檔...|  
|ErrNotCodeDomType|傳遞至指定引數的指定型別不屬於指定的衍生類別。|  
|WrnNoTypeForServices|傳遞的組件沒有一個包含使用指定組態名稱的服務類型。|  
|ErrAssemblyLoadFailed|無法將指定檔案當成組件載入。 如需詳細資訊，請檢查 FusionLogs。|  
|NoMetadataWasGenerated|未產生任何中繼資料檔。 未匯出任何服務合約。<br /><br /> 若要匯出合約，請使用指定選項。 若要匯出資料合約，請指定選項。|  
|WrnCannotResolveServiceForExport|無法載入包含指定 configName 的服務。 若要匯出服務，請提供包含服務類型的組件，以及包含此服務組態的可執行檔。|  
|ParametersCollectionType|\<type>|  
|ErrOptionConflictsWithTarget|設為指定值的指定選項不支援使用指定選項。|  
|ErrCodegenError|以指定語言產生程式碼時發生錯誤。<br /><br /> 該語言不支援所有正在產生的程式碼項目。 您應該使用其他語言。|  
|ErrInputWsdlParseError|讀取指定項目時發生 WSDL 剖析錯誤。 請驗證 XML 格式正確而且有效。|  
|ErrCouldNotCreateInstance|無法針對已傳送至指定引數的指定型別建立其執行個體。|  
|ParametersNamespace|\<字串、 字串 >|  
|HelpNostdlib|請勿參照標準程式庫 (根據預設會參照 mscorlib.dll 與 system.servicemodel.dll)。|  
|WrnCannotLoadConfigFileForExport|在處理從指定位置載入的組態檔時發生錯誤。 無法載入在此組態檔中定義的服務。|  
|WrnUnableToLoadContractForExport|載入合約類型時發生錯誤。 無法匯出這個指定型別。|
