---
title: "SerializationBinder를 사용하여 serialization 및 deserialization 제어 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# SerializationBinder를 사용하여 serialization 및 deserialization 제어
serialization 도중에, 포맷터는 올바른 형식 및 버전의 개체 인스턴스를 만드는 데 필요한 정보를 전송합니다.  이 정보에는 일반적으로 개체에 대한 어셈블리 이름 및 전체 형식 이름이 포함됩니다.  기본적으로 deserialization은 이 정보를 사용하여 동일한 개체의 인스턴스를 만듭니다.  deserialization을 수행하는 컴퓨터에 원본 클래스가 없거나, 원본 클래스가 어셈블리 간에 이동했거나, 서버와 클라이언트에 서로 다른 버전의 클래스가 필요한 경우 일부 사용자는 serialize 및 deserialize할 클래스를 제어해야 할 수 있습니다.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Serialization 바인더 사용](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  이 기능은 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 또는 <xref:System.Runtime.Serialization.NetDataContractSerializer>를 사용할 때만 사용할 수 있습니다.  
  
## SerializationBinder 사용  
 <xref:System.Runtime.Serialization.SerializationBinder>는 serialization 및 deserialization 중에 사용되는 실제 형식을 제어하는 데 사용되는 추상 클래스입니다.  serialization 및 deserialization 중에 사용되는 형식을 제어하려면 <xref:System.Runtime.Serialization.SerializationBinder>에서 클래스를 파생시키고 <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False&autoUpgrade=True 및 <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False&autoUpgrade=True 메서드를 재정의합니다.  <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False&autoUpgrade=True 메서드는 <xref:System.Type>을 받아서 어셈블리 및 형식 이름을 반환합니다.  <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False&autoUpgrade=True 메서드는 어셈블리 및 형식 이름을 받아서 <xref:System.Type>을 반환합니다.  
  
## 참고 항목  
 [Serialization 및 Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)   
 [Serialization 바인더 사용](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)