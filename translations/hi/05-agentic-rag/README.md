<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "7622aa72f9e676e593339f5f694ecd7d",
  "translation_date": "2025-05-20T09:44:25+00:00",
  "source_file": "05-agentic-rag/README.md",
  "language_code": "hi"
}
-->
[![Agentic RAG](../../../translated_images/lesson-5-thumbnail.1bab9551989766fa0dbea97c250a68c41e0f36ed9b02d3aa8ee8fdcc62596981.hi.png)](https://youtu.be/WcjAARvdL7I?si=BCgwjwFb2yCkEhR9)

> _(इस पाठ का वीडियो देखने के लिए ऊपर दिए गए चित्र पर क्लिक करें)_

# Agentic RAG

यह पाठ Agentic Retrieval-Augmented Generation (Agentic RAG) का एक व्यापक परिचय प्रदान करता है, जो एक उभरता हुआ AI दृष्टिकोण है जहाँ बड़े भाषा मॉडल (LLMs) स्वायत्त रूप से अपने अगले कदमों की योजना बनाते हैं और बाहरी स्रोतों से जानकारी प्राप्त करते हैं। स्थिर retrieval-then-read पैटर्न के विपरीत, Agentic RAG में LLM को बार-बार कॉल किया जाता है, जिसके बीच में टूल या फंक्शन कॉल और संरचित आउटपुट होते हैं। सिस्टम परिणामों का मूल्यांकन करता है, क्वेरी को परिष्कृत करता है, जरूरत पड़ने पर अतिरिक्त टूल्स को सक्रिय करता है, और तब तक यह चक्र जारी रखता है जब तक कि एक संतोषजनक समाधान प्राप्त न हो जाए।

## परिचय

इस पाठ में निम्नलिखित विषय शामिल होंगे:

- **Agentic RAG को समझना:** AI में उभरते इस दृष्टिकोण के बारे में जानें जहाँ बड़े भाषा मॉडल (LLMs) स्वायत्त रूप से अपने अगले कदमों की योजना बनाते हैं और बाहरी डेटा स्रोतों से जानकारी प्राप्त करते हैं।
- **इटरेटिव मेकर-चेकर स्टाइल को समझना:** LLM को बार-बार कॉल करने के चक्र को समझें, जिसमें टूल या फंक्शन कॉल और संरचित आउटपुट शामिल होते हैं, जो सही उत्तर सुनिश्चित करने और गलत क्वेरी को संभालने के लिए डिज़ाइन किया गया है।
- **व्यावहारिक अनुप्रयोगों की खोज:** उन परिस्थितियों की पहचान करें जहाँ Agentic RAG सबसे अधिक प्रभावी होता है, जैसे कि correctness-first वातावरण, जटिल डेटाबेस इंटरैक्शन, और विस्तारित वर्कफ़्लो।

## सीखने के लक्ष्य

इस पाठ को पूरा करने के बाद, आप निम्नलिखित समझेंगे:

- **Agentic RAG की समझ:** AI में इस उभरते दृष्टिकोण को जानें जहाँ बड़े भाषा मॉडल स्वायत्त रूप से अगले कदम योजना बनाते हैं और बाहरी डेटा स्रोतों से जानकारी निकालते हैं।
- **इटरेटिव मेकर-चेकर स्टाइल:** LLM को बार-बार कॉल करने के चक्र को समझें, जिसमें टूल या फंक्शन कॉल और संरचित आउटपुट शामिल होते हैं, जो सही उत्तर सुनिश्चित करते हैं और गलत क्वेरी को संभालते हैं।
- **तर्क प्रक्रिया का स्वामित्व:** सिस्टम की अपनी तर्क प्रक्रिया को नियंत्रित करने की क्षमता को समझें, जो पूर्वनिर्धारित मार्गों पर निर्भर नहीं करता।
- **वर्कफ़्लो:** समझें कि एक एजेंटिक मॉडल कैसे स्वतंत्र रूप से मार्केट ट्रेंड रिपोर्ट्स प्राप्त करता है, प्रतिस्पर्धी डेटा की पहचान करता है, आंतरिक बिक्री मेट्रिक्स को सहसंबंधित करता है, निष्कर्षों को समेकित करता है, और रणनीति का मूल्यांकन करता है।
- **इटरेटिव लूप, टूल इंटीग्रेशन, और मेमोरी:** जानें कि सिस्टम कैसे एक लूपेड इंटरैक्शन पैटर्न पर निर्भर करता है, जो स्टेट और मेमोरी को बनाए रखता है ताकि पुनरावृत्ति से बचा जा सके और सूचित निर्णय लिए जा सकें।
- **फेल्योर मोड और सेल्फ-करेक्शन का प्रबंधन:** सिस्टम के मजबूत आत्म-संशोधन तंत्रों का अन्वेषण करें, जिसमें पुनरावृत्ति, पुनः क्वेरी करना, डायग्नोस्टिक टूल्स का उपयोग, और मानव निरीक्षण शामिल हैं।
- **एजेंसी की सीमाएँ:** Agentic RAG की सीमाओं को समझें, जिसमें डोमेन-विशिष्ट स्वायत्तता, इन्फ्रास्ट्रक्चर पर निर्भरता, और गार्डरेल्स का सम्मान शामिल है।
- **व्यावहारिक उपयोग और मूल्य:** उन परिस्थितियों की पहचान करें जहाँ Agentic RAG सबसे प्रभावी होता है, जैसे correctness-first वातावरण, जटिल डेटाबेस इंटरैक्शन, और विस्तारित वर्कफ़्लो।
- **गवर्नेंस, पारदर्शिता, और विश्वास:** गवर्नेंस और पारदर्शिता के महत्व को समझें, जिसमें व्याख्यायोग्य तर्क, पूर्वाग्रह नियंत्रण, और मानव निरीक्षण शामिल हैं।

## Agentic RAG क्या है?

Agentic Retrieval-Augmented Generation (Agentic RAG) एक उभरता हुआ AI दृष्टिकोण है जहाँ बड़े भाषा मॉडल (LLMs) स्वायत्त रूप से अपने अगले कदमों की योजना बनाते हैं और बाहरी स्रोतों से जानकारी प्राप्त करते हैं। स्थिर retrieval-then-read पैटर्न के विपरीत, Agentic RAG में LLM को बार-बार कॉल किया जाता है, जिसके बीच में टूल या फंक्शन कॉल और संरचित आउटपुट होते हैं। सिस्टम परिणामों का मूल्यांकन करता है, क्वेरी को परिष्कृत करता है, जरूरत पड़ने पर अतिरिक्त टूल्स को सक्रिय करता है, और तब तक यह चक्र जारी रखता है जब तक कि एक संतोषजनक समाधान प्राप्त न हो जाए। यह इटरेटिव “मेकर-चेकर” शैली सहीपन को बढ़ाती है, गलत क्वेरियों को संभालती है, और उच्च गुणवत्ता वाले परिणाम सुनिश्चित करती है।

सिस्टम अपनी तर्क प्रक्रिया का सक्रिय रूप से स्वामित्व लेता है, विफल क्वेरियों को पुनः लिखता है, विभिन्न पुनर्प्राप्ति विधियाँ चुनता है, और कई टूल्स को एकीकृत करता है—जैसे Azure AI Search में वेक्टर सर्च, SQL डेटाबेस, या कस्टम API—अपने उत्तर को अंतिम रूप देने से पहले। एक एजेंटिक सिस्टम की मुख्य विशेषता इसकी तर्क प्रक्रिया का स्वामित्व है। पारंपरिक RAG कार्यान्वयन पूर्वनिर्धारित मार्गों पर निर्भर करते हैं, लेकिन एक एजेंटिक सिस्टम सूचना की गुणवत्ता के आधार पर कदमों के अनुक्रम को स्वायत्त रूप से निर्धारित करता है।

## Agentic Retrieval-Augmented Generation (Agentic RAG) की परिभाषा

Agentic Retrieval-Augmented Generation (Agentic RAG) AI विकास में एक उभरता हुआ दृष्टिकोण है जहाँ LLM न केवल बाहरी डेटा स्रोतों से जानकारी प्राप्त करते हैं, बल्कि स्वायत्त रूप से अपने अगले कदमों की योजना भी बनाते हैं। स्थिर retrieval-then-read पैटर्न या सावधानीपूर्वक स्क्रिप्टेड प्रॉम्प्ट अनुक्रमों के विपरीत, Agentic RAG में LLM को बार-बार कॉल किया जाता है, जिसमें टूल या फंक्शन कॉल और संरचित आउटपुट होते हैं। हर चरण पर, सिस्टम प्राप्त परिणामों का मूल्यांकन करता है, यह तय करता है कि क्या क्वेरी को परिष्कृत करना है, जरूरत पड़ने पर अतिरिक्त टूल्स को सक्रिय करता है, और तब तक यह चक्र जारी रखता है जब तक कि एक संतोषजनक समाधान न मिल जाए।

यह इटरेटिव “मेकर-चेकर” शैली ऑपरेशन को सहीपन बढ़ाने, संरचित डेटाबेस (जैसे NL2SQL) के लिए गलत क्वेरियों को संभालने, और संतुलित, उच्च गुणवत्ता वाले परिणाम सुनिश्चित करने के लिए डिज़ाइन किया गया है। केवल सावधानीपूर्वक निर्मित प्रॉम्प्ट चेन पर निर्भर रहने के बजाय, सिस्टम अपनी तर्क प्रक्रिया का सक्रिय रूप से स्वामित्व लेता है। यह विफल क्वेरियों को पुनः लिख सकता है, विभिन्न पुनर्प्राप्ति विधियाँ चुन सकता है, और कई टूल्स को एकीकृत कर सकता है—जैसे Azure AI Search में वेक्टर सर्च, SQL डेटाबेस, या कस्टम API—अपने उत्तर को अंतिम रूप देने से पहले। इससे अत्यधिक जटिल ऑर्केस्ट्रेशन फ्रेमवर्क की आवश्यकता समाप्त हो जाती है। इसके बजाय, एक अपेक्षाकृत सरल लूप “LLM कॉल → टूल उपयोग → LLM कॉल → …” परिष्कृत और ठोस आउटपुट दे सकता है।

![Agentic RAG Core Loop](../../../translated_images/agentic-rag-core-loop.2224925a913fb3439f518bda61a40096ddf6aa432a11c9b5bba8d0d625e47b79.hi.png)

## तर्क प्रक्रिया का स्वामित्व

जिस विशेषता से कोई सिस्टम “agentic” कहलाता है, वह इसकी अपनी तर्क प्रक्रिया का स्वामित्व लेने की क्षमता है। पारंपरिक RAG कार्यान्वयन अक्सर मानवों द्वारा मॉडल के लिए एक मार्ग पूर्वनिर्धारित करने पर निर्भर करते हैं: एक chain-of-thought जो बताता है कि क्या और कब पुनर्प्राप्त करना है।
लेकिन जब कोई सिस्टम वास्तव में agentic होता है, तो वह आंतरिक रूप से यह तय करता है कि समस्या को कैसे हल करना है। यह केवल एक स्क्रिप्ट का पालन नहीं कर रहा होता; यह सूचना की गुणवत्ता के आधार पर कदमों के अनुक्रम को स्वायत्त रूप से निर्धारित करता है।
उदाहरण के लिए, यदि इसे एक उत्पाद लॉन्च रणनीति बनाने के लिए कहा जाता है, तो यह केवल उस प्रॉम्प्ट पर निर्भर नहीं करता जो पूरी शोध और निर्णय प्रक्रिया को स्पष्ट करता है। इसके बजाय, एजेंटिक मॉडल स्वतंत्र रूप से निर्णय लेता है कि:

1. Bing Web Grounding का उपयोग करके वर्तमान बाजार ट्रेंड रिपोर्ट प्राप्त करें।
2. Azure AI Search का उपयोग करके प्रासंगिक प्रतिस्पर्धी डेटा की पहचान करें।
3. Azure SQL Database का उपयोग करके ऐतिहासिक आंतरिक बिक्री मेट्रिक्स को सहसंबंधित करें।
4. Azure OpenAI Service के माध्यम से निष्कर्षों को समेकित रणनीति में संकलित करें।
5. रणनीति का मूल्यांकन करें, यदि आवश्यक हो तो पुनः प्राप्ति के लिए प्रेरित करें।
ये सभी कदम—क्वेरी को परिष्कृत करना, स्रोत चुनना, जब तक उत्तर से “संतुष्ट” न हो जाए तब तक पुनरावृत्ति करना—मॉडल द्वारा तय किए जाते हैं, न कि मानव द्वारा पूर्वनिर्धारित।

## इटरेटिव लूप, टूल इंटीग्रेशन, और मेमोरी

![Tool Integration Architecture](../../../translated_images/tool-integration.7b05a923e3278bf1fd2972faa228fb2ac725f166ed084362b031a24bffd26287.hi.png)

एक एजेंटिक सिस्टम एक लूपेड इंटरैक्शन पैटर्न पर निर्भर करता है:

- **प्रारंभिक कॉल:** उपयोगकर्ता का लक्ष्य (अर्थात् उपयोगकर्ता प्रॉम्प्ट) LLM को प्रस्तुत किया जाता है।
- **टूल सक्रियण:** यदि मॉडल को जानकारी की कमी या अस्पष्ट निर्देश मिलते हैं, तो यह एक टूल या पुनर्प्राप्ति विधि चुनता है—जैसे वेक्टर डेटाबेस क्वेरी (जैसे Azure AI Search Hybrid सर्च निजी डेटा पर) या संरचित SQL कॉल—अधिक संदर्भ प्राप्त करने के लिए।
- **मूल्यांकन और परिष्करण:** प्राप्त डेटा की समीक्षा के बाद, मॉडल यह तय करता है कि जानकारी पर्याप्त है या नहीं। यदि नहीं, तो यह क्वेरी को परिष्कृत करता है, कोई दूसरा टूल आजमाता है, या अपनी रणनीति समायोजित करता है।
- **तृप्ति तक पुनरावृत्ति:** यह चक्र तब तक जारी रहता है जब तक मॉडल यह निर्धारित नहीं कर लेता कि उसके पास एक अंतिम, सुविचारित उत्तर देने के लिए पर्याप्त स्पष्टता और प्रमाण हैं।
- **मेमोरी और स्टेट:** चूंकि सिस्टम स्टेप्स के बीच स्टेट और मेमोरी बनाए रखता है, यह पिछले प्रयासों और उनके परिणामों को याद रख सकता है, पुनरावृत्ति से बचता है और आगे बढ़ते हुए अधिक सूचित निर्णय लेता है।

समय के साथ, यह समझ की एक विकसित भावना बनाता है, जिससे मॉडल जटिल, बहु-चरण कार्यों को बिना मानव हस्तक्षेप या प्रॉम्प्ट को बार-बार संशोधित किए नेविगेट कर सकता है।

## फेल्योर मोड और सेल्फ-करेक्शन का प्रबंधन

Agentic RAG की स्वायत्तता में मजबूत आत्म-संशोधन तंत्र भी शामिल हैं। जब सिस्टम को मृत अंत का सामना करना पड़ता है—जैसे अप्रासंगिक दस्तावेज़ प्राप्त करना या गलत क्वेरी का सामना करना—तो यह:

- **पुनरावृत्ति और पुनः क्वेरी:** कम मूल्य वाले उत्तर देने के बजाय, मॉडल नई खोज रणनीतियाँ आजमाता है, डेटाबेस क्वेरियों को पुनः लिखता है, या वैकल्पिक डेटा सेट देखता है।
- **डायग्नोस्टिक टूल्स का उपयोग:** सिस्टम अतिरिक्त फंक्शंस को सक्रिय कर सकता है जो तर्क के चरणों को डिबग करने या प्राप्त डेटा की सहीता की पुष्टि करने में मदद करते हैं। Azure AI Tracing जैसे टूल मजबूत अवलोकनीयता और निगरानी सक्षम करने के लिए महत्वपूर्ण होंगे।
- **मानव निरीक्षण पर निर्भरता:** उच्च जोखिम वाले या बार-बार विफल हो रहे परिदृश्यों के लिए, मॉडल अनिश्चितता को चिन्हित कर सकता है और मानव मार्गदर्शन का अनुरोध कर सकता है। जब मानव सुधारात्मक प्रतिक्रिया प्रदान करता है, तो मॉडल उस सीख को आगे के लिए समाहित कर सकता है।

यह पुनरावृत्त और गतिशील दृष्टिकोण मॉडल को लगातार सुधारने की अनुमति देता है, यह सुनिश्चित करता है कि यह केवल एक बार चलने वाला सिस्टम नहीं है बल्कि एक ऐसा सिस्टम है जो सत्र के दौरान अपनी गलतियों से सीखता है।

![Self Correction Mechanism](../../../translated_images/self-correction.3d42c31baf4a476bb89313cec58efb196b0e97959c04d7439cc23d27ef1242ac.hi.png)

## एजेंसी की सीमाएँ

अपने कार्य के भीतर स्वायत्त होने के बावजूद, Agentic RAG कृत्रिम सामान्य बुद्धिमत्ता (Artificial General Intelligence) के समान नहीं है। इसकी “agentic” क्षमताएँ केवल टूल्स, डेटा स्रोतों, और नीतियों तक सीमित हैं जो मानव डेवलपर्स द्वारा प्रदान की गई हैं। यह अपने स्वयं के टूल्स का आविष्कार नहीं कर सकता या सेट किए गए डोमेन सीमाओं से बाहर नहीं जा सकता। बल्कि, यह उपलब्ध संसाधनों का गतिशील रूप से समन्वय करने में माहिर है।
अधिक उन्नत AI रूपों से मुख्य अंतर हैं:

1. **डोमेन-विशिष्ट स्वायत्तता:** Agentic RAG सिस्टम उपयोगकर्ता-परिभाषित लक्ष्यों को ज्ञात डोमेन के भीतर प्राप्त करने पर केंद्रित होते हैं, क्वेरी पुनःलेखन या टूल चयन जैसी रणनीतियों का उपयोग करके परिणामों में सुधार करते हैं।
2. **इन्फ्रास्ट्रक्चर-निर्भर:** सिस्टम की क्षमताएँ डेवलपर्स द्वारा एकीकृत टूल्स और डेटा पर निर्भर करती हैं। यह मानव हस्तक्षेप के बिना इन सीमाओं से बाहर नहीं जा सकता।
3. **गार्डरेल्स का सम्मान:** नैतिक दिशानिर्देश, अनुपालन नियम, और व्यापार नीतियाँ बहुत महत्वपूर्ण रहती हैं। एजेंट की स्वतंत्रता हमेशा सुरक्षा उपायों और निरीक्षण तंत्रों से सीमित होती है (आशा है कि)।

## व्यावहारिक उपयोग के मामले और मूल्य

Agentic RAG उन परिदृश्यों में चमकता है जहाँ पुनरावृत्ति और सटीकता आवश्यक होती है:

1. **सहीपन-प्रथम वातावरण:** अनुपालन जांच, नियामक विश्लेषण, या कानूनी शोध में, एजेंटिक मॉडल बार-बार तथ्यों की पुष्टि कर सकता है, कई स्रोतों से परामर्श कर सकता है, और तब तक क्वेरियों को पुनः लिख सकता है जब तक कि वह पूरी तरह से सत्यापित उत्तर न दे।
2. **जटिल डेटाबेस इंटरैक्शन:** संरचित डेटा के साथ काम करते समय जहाँ क्वेरियाँ अक्सर विफल हो सकती हैं या समायोजन की आवश्यकता हो सकती है, सिस्टम स्वायत्त रूप से Azure SQL या Microsoft Fabric OneLake का उपयोग करके अपनी क्वेरियों को परिष्कृत कर सकता है, जिससे अंतिम पुनर्प्राप्ति उपयोगकर्ता की मंशा के अनुरूप हो।
3. **विस्तारित वर्कफ़्लो:** लंबे चलने वाले सत्र नए डेटा के आने के साथ विकसित हो सकते हैं। Agentic RAG लगातार नए डेटा को समाहित कर सकता है, और जैसे-जैसे यह समस्या क्षेत्र के बारे में अधिक जानता है, अपनी रणनीतियाँ बदल सकता है।

## गवर्नेंस, पारदर्शिता, और विश्वास

जैसे-जैसे ये सिस्टम अपनी तर्क क्षमता में अधिक स्वायत्त होते जाते हैं, गवर्नेंस और पारदर्शिता महत्वपूर्ण हो जाती हैं:

- **व्याख्यायोग्य तर्क:** मॉडल उन क्वेरियों का ऑडिट ट्रेल प्रदान कर सकता है जो उसने कीं, जिन स्रोतों से उसने परामर्श किया, और तर्क के चरण जो उसने अपनी निष्कर्ष तक पहुँचने के लिए अपनाए। Azure AI Content Safety और Azure AI Tracing / GenAIOps जैसे टूल पारदर्शिता बनाए रखने और जोखिम कम करने में मदद करते हैं।
- **पूर्वाग्रह नियंत्रण और संतुलित पुनर्प्राप्ति:** डेवलपर्स पुनर्प्राप्ति रणनीतियों को इस तरह से ट्यून कर सकते हैं कि संतुलित, प्रतिनिधि डेटा स्रोतों पर विचार किया जाए, और नियमित रूप से आउटपुट का ऑडिट कर सकते हैं ताकि पूर्वाग्रह या विकृत पैटर्न का पता चल सके, विशेष रूप से Azure Machine Learning का उपयोग करने वाले उन्नत डेटा साइंस संगठनों के लिए।
- **मानव निरीक्षण और अनुपालन:** संवेदनशील कार्यों के लिए, मानव समीक्षा आवश्यक रहती है। Agentic RAG उच्च जोखिम वाले निर्णयों में मानव निर्णय को प्रतिस्थापित नहीं करता—बल्कि इसे अधिक पूरी तरह से सत्यापित विकल्प प्रदान करके बढ़ाता है।

ऐसे टूल्स का होना जो क्रियाओं का स्पष्ट रिकॉर्ड प्रदान करें आवश्यक है। इनके बिना, बहु-चरण प्रक्रिया का डिबगिंग बहुत कठिन हो सकता है। नीचे Literal AI (Chainlit के पीछे कंपनी) के एक एजेंट रन का उदाहरण देखें:

![AgentRunExample](../../../translated_images/AgentRunExample.27e2df23ad898772d1b3e7a3e3cd4615378e10dfda87ae8f06b4748bf8eea97d.hi.png)

![AgentRunExample2](../../../translated_images/AgentRunExample2.c0e8c78b1f2540a641515e60035abcc6a9c5e3688bae143eb6c559dd37cdee9f.hi.png)

## निष्कर्ष

Agentic RAG AI सिस्टमों के जटिल, डेटा-गहन कार्यों को संभालने के तरीके में एक प्राकृतिक विकास का प्रतिनिधित्व करता है। लूपेड इंटरैक्शन पैटर्न अपनाकर, टूल्स का स्वायत्त चयन करके, और क्वेरियों को तब तक परिष्कृत करके जब तक उच्च गुणवत्ता वाला परिणाम न मिल जाए, यह सिस्टम स्थिर प्रॉम्प्ट-फॉलोइंग से आगे बढ़कर एक अधिक अनुकूली, संदर्भ-सचेत निर्णय निर्माता बन जाता है। जबकि यह अभी भी मानव-परिभाषित इन्फ्रास्ट्रक्चर और नैतिक दिशानिर्देशों द्वारा सीमित है, ये

**अस्वीकरण**:  
यह दस्तावेज़ AI अनुवाद सेवा [Co-op Translator](https://github.com/Azure/co-op-translator) का उपयोग करके अनुवादित किया गया है। जबकि हम सटीकता के लिए प्रयासरत हैं, कृपया ध्यान दें कि स्वचालित अनुवादों में त्रुटियाँ या अशुद्धियाँ हो सकती हैं। मूल दस्तावेज़ को उसकी मूल भाषा में प्रामाणिक स्रोत माना जाना चाहिए। महत्वपूर्ण जानकारी के लिए, पेशेवर मानव अनुवाद की सलाह दी जाती है। इस अनुवाद के उपयोग से उत्पन्न किसी भी गलतफहमी या गलत व्याख्या के लिए हम जिम्मेदार नहीं हैं।