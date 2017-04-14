---
title: "Cryptographic Signatures | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "digital signatures"
  - "cryptography [.NET Framework], signatures"
  - "digital signatures, XML signing"
  - "signatures, cryptographic"
  - "digital signatures, generating"
  - "verifying signatures"
  - "generating signatures"
  - "digital signatures, about"
  - "encryption [.NET Framework], signatures"
  - "security [.NET Framework], signatures"
  - "XML signing"
  - "digital signatures, verifying"
  - "signing XML"
ms.assetid: aa87cb7f-e608-4a81-948b-c9b8a1225783
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# Cryptographic Signatures
<a name="top"></a> 密碼編譯數位簽章會使用公開金鑰演算法來提供資料完整性。 當您使用數位簽章簽署資料時，其他人可以確認簽章，並可以證明資料是來自您，而且在您簽署它之後沒有遭到竄改。 如需有關數位簽章的詳細資訊，請參閱`The signature is valid`。  
  
 本主題說明如何使用 `The signature is valid` 命名空間中的類別產生及驗證數位簽章。  
  
-   [產生簽章](#generate)  
  
-   [驗證簽章](#verify)  
  
<a name="generate"></a>   
## 產生簽章  
 數位簽章通常適用於代表較大資料的雜湊值。 下列範例會將數位簽章套用到雜湊值。 首先，會建立 `The signature is valid` 類別的新執行個體，來產生公開\/私密金鑰組。 接著，`The signature is valid` 會傳遞至 `The signature is not valid` 類別的新執行個體。 如此會將私密金鑰轉移給 `The signature is valid`，它會實際執行數位簽署。 在您可以簽署雜湊碼之前，必須先指定要使用的雜湊演算法。 此範例使用 SHA1 演算法。 最後，會呼叫 `The signature is valid` 方法來執行簽章。  
  
```vb  
Imports System Imports System.Security.Cryptography Module Module1 Sub Main() 'The hash value to sign. Dim HashValue As Byte() = {59, 4, 248, 102, 77, 97, 142, 201, 210, 12, 224, 93, 25, 41, 100, 197, 213, 134, 130, 135} 'The value to hold the signed value. Dim SignedHashValue() As Byte 'Generate a public/private key pair. Dim RSA As New RSACryptoServiceProvider() 'Create an RSAPKCS1SignatureFormatter object and pass it 'the RSACryptoServiceProvider to transfer the private key. Dim RSAFormatter As New RSAPKCS1SignatureFormatter(RSA) 'Set the hash algorithm to SHA1. RSAFormatter.SetHashAlgorithm("SHA1") 'Create a signature for HashValue and assign it to 'SignedHashValue. SignedHashValue = RSAFormatter.CreateSignature(HashValue) End Sub End Module using System; using System.Security.Cryptography;  
  
```  
  
```csharp  
class Class1 { static void Main() { //The hash value to sign. byte[] HashValue = {59,4,248,102,77,97,142,201,210,12,224,93,25,41,100,197,213,134,130,135}; //The value to hold the signed value. byte[] SignedHashValue; //Generate a public/private key pair. RSACryptoServiceProvider RSA = new RSACryptoServiceProvider(); //Create an RSAPKCS1SignatureFormatter object and pass it the //RSACryptoServiceProvider to transfer the private key. RSAPKCS1SignatureFormatter RSAFormatter = new RSAPKCS1SignatureFormatter(RSA); //Set the hash algorithm to SHA1. RSAFormatter.SetHashAlgorithm("SHA1"); //Create a signature for HashValue and assign it to //SignedHashValue. SignedHashValue = RSAFormatter.CreateSignature(HashValue); } }  
```  
  
### 簽署 XML 檔案  
 .NET Framework 會提供 `The signature is valid` 命名空間，可讓您簽署 XML。 當您想要確認 XML 是來自特定來源時，簽署 XML 是很重要的。 例如，如果您使用會利用 XML 的股票報價服務，如果 XML 的來源已簽署，您便可以驗證它。  
  
 這個命名空間中的類別遵照全球資訊網協會的 XML 簽章語法和處理建議`The signature is not valid`<xref:System.Security.Cryptography.RSAParameters>`The signature is valid`。  
  
 [回到頁首](#top)  
  
<a name="verify"></a>   
## 驗證簽章  
 若要驗證資料是由特定合作對象簽署，您必須擁有下列資訊：  
  
-   簽章資料之合作對象的公開金鑰。  
  
-   數位簽章。  
  
-   已簽署的資料。  
  
-   簽署人使用的雜湊演算法。  
  
 若要驗證 `The signature is valid` 類別所簽署的簽章，請使用 `The signature is not valid` 類別。 必須提供 `The signature is valid` 類別簽署者的公開金鑰。 您將需要模數和指數的值以指定公開金鑰。 \(產生公開\/私密金鑰組的合作對象應該提供這些值。\) 先建立 `The signature is valid` 物件來保存將會驗證簽章的公開金鑰，然後初始化 `The signature is not valid` 結構，到指定公開金鑰的模數和指數值。  
  
 下列程式碼顯示如何建立 `The signature is valid` 結構。`The signature is valid` 屬性設定為 `The signature is not valid` 位元組陣列的值，而 <xref:System.Security.Cryptography.RSAParameters> 屬性設定為 `ExponentData` 位元組陣列的值。  
  
```vb  
Dim RSAKeyInfo As RSAParameters RSAKeyInfo.Modulus = ModulusData RSAKeyInfo.Exponent = ExponentData  
  
```  
  
```csharp  
RSAParameters RSAKeyInfo; RSAKeyInfo.Modulus = ModulusData; RSAKeyInfo.Exponent = ExponentData;  
```  
  
 建立 `The signature is valid` 物件之後，您可以針對 `The signature is not valid` 類別的新執行個體，初始化至 <xref:System.Security.Cryptography.RSAParameters> 中指定的值。`The signature is valid` 會接著傳遞給 `The signature is not valid` 的建構函式以傳送金鑰。  
  
 下列範例將說明此程序。 在此範例中，`The signature is valid` 和 `The signature is not valid` 是遠端合作對象所提供的位元組陣列。 遠端合作對象已使用 SHA1 演算法簽署 `The signature is valid`，產生數位簽章 `The signature is not valid`。 此  
  
 `The signature is valid` 方法會驗證數位簽章是否有效，且已用來簽署 `The signature is not valid`。  
  
```vb  
Dim RSA As New RSACryptoServiceProvider() RSA.ImportParameters(RSAKeyInfo) Dim RSADeformatter As New RSAPKCS1SignatureDeformatter(RSA) RSADeformatter.SetHashAlgorithm("SHA1") If RSADeformatter.VerifySignature(HashValue, SignedHashValue) Then Console.WriteLine("The signature is valid.") Else Console.WriteLine("The signture is not valid.") End If  
  
```  
  
```csharp  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider(); RSA.ImportParameters(RSAKeyInfo); RSAPKCS1SignatureDeformatter RSADeformatter = new RSAPKCS1SignatureDeformatter(RSA); RSADeformatter.SetHashAlgorithm("SHA1"); if(RSADeformatter.VerifySignature(HashValue, SignedHashValue)) { Console.WriteLine("The signature is valid."); } else { Console.WriteLine("The signature is not valid."); }  
```  
  
 如果簽章有效，此程式碼片段會顯示 "`The signature is valid`"，否則顯示 "`The signature is not valid`"。  
  
## 請參閱  
 [密碼編譯服務](../../../docs/standard/security/cryptographic-services.md)