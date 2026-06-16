**

# 1. Introduction

Chikhi Mohamed Yahia

Autism spectrum disorder is a condition related to brain development that affects how people see others and socialize with them. This causes problems in communication and getting along with others socially. The condition also includes limited and repeated patterns of behavior. The term "spectrum" in autism spectrum disorder refers to the wide range of symptoms and the severity of these symptoms. Stats provided by the World Health Organisation in 2023 shows that about 1 in 100 children is diagnosed with ASD worldwide, with cases on the rise in developing but also developed countries throughout the past couple of years. Here in Malaysia for example, the trend also proves to be relevant, the National Autism Society of Malaysia also known as NASOM announced a 30 per cent increase in student needs in the first 6 months of 2024 alone, students requiring additional help than what’s normally provided to them, and in most cases, government run therapy centres offering this kind of assistance are still scarce, especially for lower income families or ones living in rural areas.

Despite these growing effects of Autism Spectrum Disorders, caregivers still go through a lot of challenges when it comes to getting access to instant, reliable, and cheap help. Families living in rural and suburban areas are the prime group in need, professional services are mostly present in centres in large cities, and the available support online is often not helpful or doesn’t tend to a specific need. The rise of intelligent chatbots brought instant, evidence based help to people taking care of individuals with ASD at any time and for free.

This literature review will go over three codependent research questions that serve as a theoretical base for our application AutiGuide, a proposed idea for a retrieval based intelligent chatbot for parents and people taking care of children with ASD in general. Our first question will cover already existing chatbot solutions and digital tools that are available on the market for autism caregivers. The second question goes through the efficiency but also limitations of retrieval based, template based and generative chatbot archetypes in medical, healthcare and caregiving situations. The third and final question evaluates and highlights the specific challenges that autism caregivers have to overcome when searching for reliable, trustworthy information as well as instantaneous help. All three inquiries cement the necessity of our application Autiguide as well as the technical choices made for its conception.

# 2. Are there any existing chatbots for autism caregivers support? and what are the types of existing solutions for people taking care of children with (ASD) available on the market?

Tan Ping Sheng

The climate of digital tools available for autism support has increased greatly in recent years; however, a close evaluation reveals that most solutions remain targeted towards the child rather than the caregiver, and that no dedicated intelligent system currently provides real-time, contextually appropriate caregiving guidance to parents.

For the domain of AI assistants and chatbots, Sohn, J., Lee, E., Kim, J., Oh, H., & Kim, E. (2025). analyzed the capability of large language model (LLM) chatbots by analysing 239 consultation queries submitted by autistic individuals or their families on a web-based medical consultation platform in China.Their findings showed that there is a growing demand for on-demand, precise and care-giver specific assistant, and stressed the continued of misinformation propagating in online circles regarding ASD. A supplementary effort by Polireddi et al. (2023) proposed a fuzzy-classifier-based chatbot designed to close the communication gap between patients, parents, and physicians, it noted that social stigma surrounding ASD often makes parents reluctant to seek in-person consultations, further increasing the need for accessible digital alternatives.

Looking from a clinical perspective, the Hong Kong Metropolitan University has initiated multiple trials exploring chatbot-based solutions for ASD caregivers. One pilot feasibility study, conducted in 2024, evaluates a positive psychology chatbot designed to support caregiver wellbeing, while a separate trial focuses on a chatbot assistant aimed to improve problem-solving skills in parents of children with ASD (ClinicalTrials.gov, 2024a; 2024b). While these initiatives show growing institutional support for chat-based caregiver support, they remain in an incubation phase, limited in research and testing rather than accessible for public usage.

Other than that, the wider digital therapeutics market for ASD is also experiencing rapid growth. The market evaluation was at USD 1.14 billion in 2024 and is expected to rise to USD 4,87 billion by 2033, this growth is caused by a combination of growing ASD prevalence, heightened awareness of early intervention, and increased adoption of digital health solutions (Growth Market Reports, 2025). Noteworthy commercial tools in recent years include Cognoa and Mightier, which apply evidence-based techniques to support children in behavioural modification exercises, and also Floreo, a virtual reality platform that received FDA breakthrough device designation in 2023 for its applications that specialise in building functional skills in autism therapy (BioSpace, 2024; Behavioral Health Business, 2024).

Despite this growth, a critical gap perseveres. Existing solutions are primarily child-focused therapy aids, general-purpose LLM chatbots not tailored to ASD, or involved in research studies that are not accessible to the wider public. As of now, no publicly accessible, dedicated intelligent solution exists to provide real-time, evidence-based guidance specifically to parents and caregivers managing day-to-day ASD challenges. AutiGuide is designed precisely to address this issue.

# 3. How effective are retrieval-based, template-based and generative chatbots in providing educational and emotional support for parents and caregivers of children with Autism Spectrum Disorder (ASD) and what are their limitations?

Boulifa Mohamed Salah Eddine 

In healthcare and caregiving fields, chatbots are usually divided into 3 main types: template based, retrieval based, and generative chatbots. Each one of thoese has its own advantages and its downsides. Understanding these differences is very important to decide the  choices made to develop AutiGuide.

## 3.1 Template-Based Chatbots

Template based chatbots use knowledge bases and pattern recognition methods . they answer only when what the user entered is relatively close to something already stored. compared to other chatbots methods they are the easiest to make and their responses are very predictable, but they have some limitations in making conversations. They cannot tell that the same question is asked in a different way or answer similar questions, or handle unexpected situations. Because of that, they may not seem as best choice for cases as the ASD caregivers (Jusoh et al., 2024). but, the HelpBot system developed by Jusoh et al. (2024) proved that even template based chatbots can give professional support and help to users in distress. This proves that simple architectures can still be effective when they are used the right way and in a specific domain.

## 3.2 Retrieval-Based Chatbots

Tan Ping Sheng 

Retrieval-based chatbots pick answers from a curated knowledge base by matching user intent with pre-written answers. Pandey and Sharma (2023) found that this method is best used for situations where the type of user inputs is limited and well-defined, resulting in quick and precise answers without requiring rigorous and extensive training. The same study noted, however, that retrieval-based systems can feel inflexible and struggle with intricate or open-ended questions where user intent is less certain.  

In healthcare and therapy applications, retrieval-based systems are the dominant system used. A study examining GPT-2 for therapy chatbots usage found that most existing therapy chatbots utilise retrieval-based approaches due to the controlled, verified nature of pre-written responses guarantees clinical safety and predictability, preventing any unsafe incidents involving the use of chatbots(Sharma et al., 2021). For a system like AutiGuide, where caregivers may follow advice given during an active behavioral crisis involving the child, the reliability and precision of retrieval-based responses cancel out the rigid, and sometimes awkward linguistic characteristics compared to other generative AIs. 

3.3 Generative Chatbots

Aissat Fethi Malik 

With data from large language models such as GPT, generative chatbots produce new answers using a method of machine learning. They can now hold a more flexible conversation and can handle more complex/open-ended questions. The big health care challenge they have is, unfortunately, that they hallucinate, making up plausible information that is synthetically false or even completely made up something that is well known.Giving medical guidance contexts, this is a huge risk as the guidance itself can hurt the vulnerable users as mentioned by Pandey & Sharma (2023). Additionally, problems of fairness and harm in the outputs of generative systems exist; and the requirement for large volumes of training data and time to execute computations, can prove costly and complex, especially in terms of maintenance (YourGPT, 2024).

Finally, though generative chatbots have been very promising for providing natural robust conversations, the potential inaccuracies that can come out of this sort of architecture make retrieval-based architecture the more suitable and harmless generation choice for AutiGuide for this use case. All responses are knowledge-based, validated and based on evidence (retrieval-based approach); there is no time when caregivers can't have valid and responsible information.

  

# 4. What challenges do caregivers of autistic children face when searching for trustworthy information and immediate support?

Sofiane Mohammed Gherrat 

## 4.1 Introduction

When a child is diagnosed with Autism Spectrum Disorder (ASD), their caregivers rarely find themselves on steady ground. They are suddenly dropped into a fragmented system where finding reliable information or support feels exhausting and maybe even impossible (Chu et al., 2020; Dobrogowska-Schlebusch, 2016; Mohd Hussain et al., 2022). This reality hits especially hard in Malaysia, where parents usually struggle to make sense of the initial diagnosis, let alone the struggle to approach therapy or keep the rest of family life from falling apart under the pressure (Chu et al., 2020).

We can distinguish four (4) main areas of struggle. First, we look at information and knowledge barriers and how the parents' educational background and as a probable consequence their income influences the quality of information they could reach (Chu et al., 2020; Dobrogowska-Schlebusch, 2016; Mohd Hussain et al., 2022).

Following with the correlation between trust and online health information. As pointed by many studies, families fallback on forums and top listed website to seek information about ASD (Dobrogowska-Schlebusch, 2016; Twombly et al., 2011; Mohd Hussain et al., 2022), even though some show a form of resilience to misinformation, the fact that they read a myth around caregivers' good practices for ASD children would influence their judgement in the future.

It would be wise to talk afterwards about the emotional barriers a caregiver suffers from and how social stigma affects the quality of treatment given to ASD children (Papadopoulos et al., 2019; Chu et al., 2020).

Now, shifting the question from: why do caregivers struggle with information? (dealt with in theme 1, 2, 3, 4) to why are caregivers fundamentally forced to depend on information in the first place?  
And how such vulnerability exposes parents even more to online misinformation?  
Well, the first thing that comes to mind is: structural barriers they face like the need to travel for hours to consult a single specialist or manage therapy costs (Kalkbrenner et al., 2011; Ou et al., 2015).

The pattern becomes clear, parents experience various challenges, some of them could be addressed internally through training, others would require policy changement and societal adaptation, a gap that could be filled with a tool to induce the change.

## 4.2 Thematic Analysis:

### Theme 1: Information and Knowledge Barriers:

The work done by Chu et al. (2020), Dobrogowska-Schlebusch (2016), and Mohd Hussain et al. (2022) point to an idea worth noting: the biggest problems caregivers have with finding information aren't about the search itself; they already exist before any question is asked in a forum or properly dealt with, rooted limited educational background and emotional state.

Most parents start their journey with very little understanding of autism, they get forced to navigate an environment where myths collide with reality on a daily basis, in fact parents lacking training to deal with ASD often view the condition as "bad behavior" or low effort rather than a neuro-developmental difference which pushes them to respond with discipline/correction rather than skill-building strategies. This has a major impact on the education given to children with ASD, affected parent-child bond and eroded treatment management.

Another consequence would be that parents could ignore co-occurring conditions and only focus most of their energy on repetitive/social behaviors while forgetting underlying problems like: chronic sleep disorders, gastrointestinal (GI) distress, or generalized anxiety. This shift in focus would lead to misinterpretation pushing the parents to view the challenge as the result of low effort and maybe abandon the treatment due to a lack of noticeable improvement. It leads additionally to misdirected efforts towards solving only the visible symptoms and ignoring the systematic ones which could worsen the case even more.

Another major underline is that poor educational background usually pairs with low income which creates another battle for caregivers: navigating treatment cost for ASD over a prolonged period of time.

This effectively positions the knowledge gap as a primary factor for mal-treatment and financial burdens only accentuates the problem.

  

### Theme 2: Trust and Online Health Information

Many studies consistently point to an increasing reliance on online platforms as a source of caregiving information among ASD families. Twombly et al. (2011) found that while the majority of caregivers were looking for factual guidance online, a considerable portion turned to digital communities for a sense of belonging and shared experience. This reveals that online spaces serve emotional needs as much as informational ones, and it is precisely this emotional aspect that makes caregivers more vulnerable to misinformation.

While some parents demonstrate enough critical awareness to avoid acting on unverified content, this resilience only addresses part of the problem. Passive exposure alone carries its own risk, eventually repeated exposure with misleading information gradually erodes parental confidence in medical professionals, often without the caregiver noticing the shift. This slowly shifts how caregivers relate to clinical guidance without them realizing it which further increases the knowledge gap.

Compounding this vulnerability, accessing traditional medical channels and dealing with structural barriers like: long waiting queues and the lack of specialized centers make the parents even more vulnerable to predatory health claims including anti-vaccination messages and leave them without solid alternatives (Dobrogowska-Schlebusch, 2016).

Since the real-world value of online platforms depends entirely on their accuracy (Mohd Hussain et al., 2022), simply making apps or portals more available misses the mark. What is needed instead are solutions that actively promote credible content, AI-powered solutions could play a crucial role in caregivers' education and AutiGuide is an excellent solution to fill the gap.

### Theme 3: Stigma and Emotional Barriers:

The challenges caregivers face cannot be understood in isolation from the psychological and social contexts in which they arise. Many studies consistently highlight increasing levels of stress and anxiety among caregivers of children with ASD, with social stigma only amplifying the problem.

Notably, autism-related stigma has been shown to carry a severe negative impact on the mental health of informal caregivers who were defined here as any individual who provides substantial, day-to-day care and support for an autistic person within their personal or family setting outside of any formal or paid professional role (Papadopoulos et al., 2019).

Papadopoulos et al. (2019) further identified two categories of moderating variables that influence the relationship between autism stigma and caregiver mental health outcomes: those that can be addressed through intervention and training like: self-esteem, and those that remain unchanged, including gender and financial burden. This distinction is very important, as it suggests that while some risk factors are structural and difficult to change, others represent genuine entry points for support and these would be future features of AutiGuide.

### Theme 4: Structural Context, Service Access, and Diagnosis:

The central argument of Theme 4 is that structural constraints act as the ultimate determinants that shape and maybe intensify the challenges discussed in Themes 1, 2, and 3.

In fact as theme 1 identified the lack of reliable knowledge as maybe the most imposing challenge, theme 4 puts the structural barriers at the root cause pushing parents towards misinformation. The difficulty in accessing diagnosis or therapy means that families are forced into prolonged periods of uncertainty, during which reliable information is sometimes nonexistent (Kalkbrenner et al., 2011). This absence of formal support doesn't make the parent less knowledgeable; it makes reliable knowledge unattainable. Thus, the barrier to knowledge moves from the individual parental fault to an infrastructural failure.

Where Theme 2 highlights the dangers of misinformation found online, theme 4 further supports the idea by claiming that the structural gaps force digital reliance, making it a survival mechanism. In fact, when professional care is geographically distant or financially prohibitive, the smartphone becomes the only functional alternative (positioning online knowledge seeking as a necessity, not a preference) (Kalkbrenner et al., 2011; Ou et al., 2015).

Finally, theme 3 addresses how societal stigma creates intense psychological stress, which is further detailed by theme 4 placing financial strain and diagnostic uncertainty as massive sources of external stress. These structural failures such as job loss due to caregiving demands or the prolonged anxiety from waiting for a diagnosis or when facing different day-to-day challenges add huge pressure that compounds the burden of stigma. The parent is not just struggling with social judgment; they are actively fighting economic instability and bureaucratic failure.

## 4.3 Conclusion and Rationale for AutiGuide:

The challenges facing ASD caregivers globally and in Malaysia specifically are not segmented problems, they rather form a chain of problems and weak points, each one reinforcing the next. The points of ignition were revealed to be: geographic distance from specialized centers, the exorbitant therapy costs and institutional bottlenecks limit many families from accessing formal support, forcing them into long queue lists before a diagnosis is even possible (Kalkbrenner et al., 2011; Ou et al., 2015).

Deprived of reliable channels, caregivers inevitably turn to digital platforms (by necessity, not by preference). Yet this environment offers no guidelines that control the flow of information, parents enter an online space sometimes anonymously, blindly looking for emotional support, with no solid knowledge to filter the misleading information forming a paradise to spread false claims in a population segment already suffering in silence which further exposes them as an easy prey for predatory health claims (Dobrogowska-Schlebusch, 2016). Even caregivers who show some resilience to false claims are not completely immune, the continuous exposure affects their perception towards specialists' diagnosis further impacting the quality of healthcare delivered.

What worsens this further is the psychological tax behind every decision a parent makes in response to social influences. Social stigma, financial instability generate a state of chronic stress and emotional exhaustion that gradually changes how caregivers process information (Papadopoulos et al., 2019; Chu et al., 2020) and how they maintain motivation to continue the treatment .

What emerges from this synthesis is not simply a shortage of information, (knowledge is abundant) but it is a failure to provide access to trustworthy, and context-aware support that meets caregivers where they are and HOW they are. Static websites and generic portals cannot respond to the variability of a caregiver's state. What is required is an intelligent system capable of delivering evidence-based guidance in real time, compensating for knowledge gaps, reducing cognitive load, and providing a private, non-judgmental channel for sensitive questions.

  

# 5. Conclusion

Ahmed Rana Saim 

The current literature review has identified a very strong need for a smart support system that caters specifically to the parents and caregivers of ASD-afflicted children. Most of the available solutions are only concerned with the provision of therapeutic care to autistic children, with hardly any effort having been put into creating dedicated platforms for caregivers that can be publicly accessed online. The review further concluded that retrieval-based chatbots constitute the best option for the development of healthcare-oriented applications as they provide accurate, reliable information without the dangers inherent to generative AI models.

Additionally, the results of this review showed that there are several problems associated with access to credible information and help for caregivers of ASD-afflicted children in Malaysia due to the numerous limitations imposed by geographical, economic, and infrastructural constraints in the region.

Generally, the literature has provided sufficient theoretical and practical support for the creation of AutiGuide. With its reliable and evidence-based chatbot, AutiGuide may help address current gaps and provide caregivers with useful information, which will allow them to feel more confident in addressing the various issues related to autism spectrum disorders. The future research should concentrate on exploring the effectiveness and usability of AutiGuide in practice.

**