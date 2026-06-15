
# **1. Introduction**

Chikhi Mohamed Yahia ✅

Autism spectrum disorder is a condition related to brain development that affects how people see others and socialize with them. This causes problems in communication and getting along with others socially. The condition also includes limited and repeated patterns of behavior. The term "spectrum" in autism spectrum disorder refers to the wide range of symptoms and the severity of these symptoms. Stats provided by the World Health Organisation in 2023 shows that about 1 in 100 children is diagnosed with ASD worldwide, with cases on the rise in developing but also developed countries throughout the past couple of years. Here in Malaysia for example, the trend also proves to be relevant, the National Autism Society of Malaysia also known as NASOM announced a 30 per cent increase in student needs in the first 6 months of 2024 alone, students requiring additional help than what’s normally provided to them, and in most cases, government run therapy centres offering this kind of assistance are still scarce, especially for lower income families or ones living in rural areas.

Despite these growing effects of Autism Spectrum Disorders, caregivers still go through a lot of challenges when it comes to getting access to instant, reliable, and cheap help. Families living in rural and suburban areas are the prime group in need, professional services are mostly present in centres in large cities, and the available support online is often not helpful or doesn’t tend to a specific need. The rise of intelligent chatbots brought instant, evidence based help to people taking care of individuals with ASD at any time and for free.

This literature review will go over three codependent research questions that serve as a theoretical base for our application AutiGuide, a proposed idea for a retrieval based intelligent chatbot for parents and people taking care of children with ASD in general. Our first question will cover already existing chatbot solutions and digital tools that are available on the market for autism caregivers. The second question goes through the efficiency but also limitations of retrieval based, template based and generative chatbot archetypes in medical, healthcare and caregiving situations. The third and final question evaluates and highlights the specific challenges that autism caregivers have to overcome when searching for reliable, trustworthy information as well as instantaneous help. All three inquiries cement the necessity of our application Autiguide as well as the technical choices made for its conception.

# **2. Are there any existing chatbots for autism caregivers support? and what are the types of existing solutions for people taking care of children with (ASD) available on the market?**

Yessimov Jamil 🟡

The landscape of digital tools available for autism support has expanded considerably in recent years; however, a close examination reveals that most solutions remain oriented towards the child rather than the caregiver, and that no dedicated intelligent system currently provides real-time, contextually appropriate caregiving guidance to parents.

On the chatbot and AI assistant front, Sohn, J., Lee, E., Kim, J., Oh, H., & Kim, E. (2025). assessed the effectiveness of large language model (LLM) chatbots by analysing 239 consultation queries submitted by autistic individuals or their families on a web-based medical consultation platform in China. Their findings highlighted the growing demand for on-demand, accurate, and caregiver-specific information, and underscored the persistent challenge of misinformation circulating in online discourse surrounding ASD. A complementary effort by Polireddi et al. (2023) proposed a fuzzy-classifier-based chatbot designed to bridge the communication gap between patients, parents, and physicians, noting that social stigma surrounding ASD often makes parents hesitant to seek in-person consultations, further driving demand for accessible digital alternatives.

At the clinical research level, Hong Kong Metropolitan University has initiated multiple trials exploring chatbot-based interventions for ASD caregivers. One pilot feasibility study, registered in 2024, examines a positive psychology chatbot designed to promote caregiver wellbeing, while a separate recruiting trial focuses on a chatbot assistant intended to improve problem-solving skills in parents of children with ASD (ClinicalTrials.gov, 2024a; 2024b). While these initiatives demonstrate growing institutional interest in chatbot-based caregiver support, they remain in the research phase and are not yet publicly available tools.

The broader digital therapeutics market for ASD is experiencing rapid growth. The global market was valued at USD 1.14 billion in 2024 and is projected to reach USD 4.87 billion by 2033, driven by rising ASD prevalence, growing awareness of early intervention, and increased adoption of digital health solutions (Growth Market Reports, 2025). Notable commercial tools include Cognoa and Mightier, which utilise evidence-based techniques to support children in behavioural modification exercises, and Floreo, a virtual reality platform that received FDA breakthrough device designation in 2023 for its skill-building applications in autism therapy (BioSpace, 2024; Behavioral Health Business, 2024).

Despite this growth, a critical gap persists. Existing solutions are primarily child-directed therapy aids, general-purpose LLM chatbots not tailored to ASD, or clinical studies still in progress. No publicly accessible, dedicated intelligent system currently provides real-time, evidence-based guidance specifically to parents and caregivers managing day-to-day ASD challenges. AutiGuide is designed precisely to address this gap.

# **3. How effective are retrieval-based, template-based and generative chatbots in providing educational and emotional support for parents and caregivers of children with Autism Spectrum Disorder (ASD) and what are their limitations?**

Boulifa Mohamed Salah Eddine 🟡

Chatbots used in healthcare and caregiving contexts are generally classified into three architectural approaches: template-based, retrieval-based, and generative. Understanding the strengths and limitations of each is essential for justifying the design decisions behind AutiGuide.

## **3.1 Template-Based Chatbots**

Template-based chatbots operate using predefined rules and pattern-matching logic, responding only when user input matches a programmed trigger. While straightforward to implement and highly predictable in output, they are severely limited in conversational flexibility. They cannot handle variations in phrasing, contextual follow-up questions, or unanticipated queries, making them insufficient for the diverse and emotionally nuanced needs of ASD caregivers (Jusoh et al., 2024). Nevertheless, the HelpBot system developed by Jusoh et al. (2024) demonstrated that even template-based NLP systems can deliver timely and professionally appropriate support to users experiencing distress, confirming that simplified architectures can be clinically effective when deployed in well-scoped domains.

## **3.2 Retrieval-Based Chatbots**

Tan Ping Sheng ✅

Retrieval-based chatbots pick answers from a curated knowledge base by matching user intent with pre-written answers. Pandey and Sharma (2023) found that this method is best used for situations where the type of user inputs is limited and well-defined, resulting in quick and precise answers without requiring rigorous and extensive training. The same study noted, however, that retrieval-based systems can feel inflexible and struggle with intricate or open-ended questions where user intent is less certain.  

In healthcare and therapy applications, retrieval-based systems are the dominant system used. A study examining GPT-2 for therapy chatbots usage found that most existing therapy chatbots utilise retrieval-based approaches due to the controlled, verified nature of pre-written responses guarantees clinical safety and predictability, preventing any unsafe incidents involving the use of chatbots(Sharma et al., 2021). For a system like AutiGuide, where caregivers may follow advice given during an active behavioral crisis involving the child, the reliability and precision of retrieval-based responses cancel out the rigid, and sometimes awkward linguistic characteristics compared to other generative AIs. 

**3.3 Generative Chatbots**

Aissat Fethi Malik ✅

With data from large language models such as GPT, generative chatbots produce new answers using a method of machine learning. They can now hold a more flexible conversation and can handle more complex/open-ended questions. The big health care challenge they have is, unfortunately, that they hallucinate, making up plausible information that is synthetically false or even completely made up something that is well known.Giving medical guidance contexts, this is a huge risk as the guidance itself can hurt the vulnerable users as mentioned by Pandey & Sharma (2023). Additionally, problems of fairness and harm in the outputs of generative systems exist; and the requirement for large volumes of training data and time to execute computations, can prove costly and complex, especially in terms of maintenance (YourGPT, 2024).

Finally, though generative chatbots have been very promising for providing natural robust conversations, the potential inaccuracies that can come out of this sort of architecture make retrieval-based architecture the more suitable and harmless generation choice for AutiGuide for this use case. All responses are knowledge-based, validated and based on evidence (retrieval-based approach); there is no time when caregivers can't have valid and responsible information.

  
  

# **4. What challenges do caregivers of autistic children face when searching for trustworthy information and immediate support?**

Sofiane Mohammed Gherrat 🟡

A substantial body of research documents the significant challenges caregivers of autistic children face when seeking trustworthy information and immediate support. These challenges are particularly pronounced in Malaysia, where structural and geographical barriers compound the already demanding nature of ASD caregiving.

#### Yaacob -> 4 main challenges

A landmark qualitative study by Yaacob, W. N. W., Yaacob, L. H. (2021)  interviewed 21 Malaysian parents of 24 children with ASD and identified four main categories of challenge: inadequate knowledge, psychological distress and stigma, lack of support, and barriers to services. The study highlighted that most public and private centres for children with ASD are concentrated in urban areas, resulting in delayed diagnosis and treatment for families in rural and suburban regions. Parents in these areas also described healthcare providers who lacked sufficient knowledge of ASD, forcing them to rely on informal and often unreliable sources.

#### ASD centers, Access, delay, following 1st paragraph 

The Malaysian healthcare infrastructure is under increasing strain. The Star (2024) reported that government-run therapy centres for autistic children remain critically insufficient, leaving lower-income families unable to access or afford private alternatives. This systemic under-provision is worsening: NASOM reported a 30 per cent surge in student needs in the first half of 2024, with placement remaining a persistent challenge that directly hinders children's development and access to appropriate care (Sinar Daily, 2024).

#### Skill gap, Day-to-Day challenges 

At the day-to-day caregiving level, the challenges are equally severe. A systematic review of studies published between 2019 and 2024 found that Malaysian caregivers frequently encounter difficulties managing meltdowns, sensory processing issues, and wandering risks. These challenges contribute to heightened caregiver stress, anxiety, and social isolation. The review further noted that although behavioural therapies and early intervention services show clinical promise, their effectiveness is routinely undermined by inconsistent implementation, resource scarcity, and the absence of standardised caregiver training (Sciety, 2025).

#### Global: train, delayed screening, policy gap
#### Financial hardships (repeated)

Globally, Scattoni et al. (2023, as cited in ScienceDirect, 2026) echo these findings, identifying that major barriers prevent caregivers from receiving timely information, screening, diagnosis, and intervention. Researchers have called for policy harmonisation and highlighted inadequate training for healthcare providers as a systemic failure requiring urgent attention. In low-to-middle-income countries, caregivers face additional layers of financial hardship and stigma that further reduce their capacity to access support (Terol et al., 2024).

Taken together, these findings confirm a strong, evidence-based demand for a dedicated, accessible, and 24/7 available intelligent system that can provide caregivers with immediate, accurate, and empathetic guidance. AutiGuide is designed to directly address this need within the Malaysian context.

# **5. Conclusion**

Ahmed Rana Saim 🟡

This literature review has established a clear and well-supported rationale for the development of AutiGuide. The first research area demonstrated that while the digital therapeutics market for autism is growing rapidly and several chatbot-based interventions are under investigation, no publicly accessible and dedicated intelligent system currently exists to provide real-time, evidence-based caregiving guidance to parents and caregivers of children with ASD. The second research area showed that retrieval-based chatbots are the most appropriate architecture for this application, offering verifiable accuracy and clinical safety that generative models cannot currently guarantee in healthcare contexts. The third research area documented the profound and persistent challenges Malaysian and global caregivers face in accessing trustworthy information and support, reinforcing the urgency of the problem AutiGuide seeks to address.

Together, these three areas of inquiry provide a strong theoretical and empirical foundation for AutiGuide's design. By combining a validated, evidence-based knowledge base with retrieval-based natural language processing and a user-friendly web interface, AutiGuide has the potential to meaningfully reduce informational inequity for ASD caregivers across Malaysia. Future work following the development and deployment of AutiGuide should include empirical user testing sessions with targeted caregivers to evaluate response accuracy, usability, and the system's actual impact on caregiver confidence and wellbeing.

# **References**

- Arzahan, I. S. N., Jamil, P. a. S. M., & Yusof, N. a. D. M. (2025). Navigating safety and Health Challenges in autism Spectrum Disorder care in Malaysia: A Systematic Literature Review of Caregiver Perspectives and Intervention Outcomes. _Research Square_. https://doi.org/10.21203/rs.3.rs-6089146/v1
    
- BioSpace. (2024, July 25). _Autism Spectrum Disorder Market Estimated to Reach a CAGR of 5.31% during 2024-2034, Impelled by the Escalated Demand for Applied Behavior Analysis (ABA) Therapy_. https://www.biospace.com/autism-spectrum-disorder-market-estimated-to-reach-a-cagr-of-5-31-during-2024-2034-impelled-by-the-escalated-demand-for-applied-behavior-analysis-aba-therapy
    
- _Blog | YourGPT_. (n.d.). https://yourgpt.ai/blog/general/retrieval-vs-generative-chatbots-best-choice-for-your-business-in-2024
    
- Carver, C. S., Scheier, M. F., & Segerstrom, S. C. (2010). Optimism. _Clinical Psychology Review_, _30_(7), 879–889. https://doi.org/10.1016/j.cpr.2010.01.006
    
- _ClinicalTrials.gov_. (n.d.-a). https://clinicaltrials.gov/study/NCT06438120
    
- _ClinicalTrials.gov_. (n.d.-b). https://clinicaltrials.gov/study/NCT06723301
    
- Hairom, N. (2024, June 21). Malaysia sees surge in autistic children needing therapy, calls for smart centre | Sinar Daily. _Sinar Daily_. https://www.sinardaily.my/article/219030
    
- Jusoh, S., Fawareh, H. A., Kadir, R. A., & Hosseinzadeh, H. (2024). HelpBot: A Web-Based Chatbot to Handle Depression Among Adolescents. _ACM_, 149–154. https://doi.org/10.1145/3669754.3669777
    
- Larson, C., & Larson, C. (2024, March 22). _Autism Tech startups aim for FDA approval, driving efficiency, market growth_. Behavioral Health Business. https://bhbusiness.com/2024/03/18/autism-tech-startups-aim-for-fda-approval-driving-efficiency-market-growth/
    
- Online, S. (2024, April 1). Autism: Awareness growing but caregivers need more support. _The Star_. https://www.thestar.com.my/news/nation/2024/04/01/autism-awareness-growing-but-caregivers-need-more-support
    
- Pandey, S., & Sharma, S. (2023). A comparative study of retrieval-based and generative-based chatbots using Deep Learning and Machine Learning. _Healthcare Analytics_, _3_, 100198. https://doi.org/10.1016/j.health.2023.100198
    
- Pavel. (2024, January 25). A chatbot for autism support and breaking the web accessibility barrier. _Research Features_. https://researchfeatures.com/chatbot-autism-support-breaking-web-accessibility-barrier/
    
- Reports, G. M., Sharma, R., & Reports, G. M. (2025, August 29). Digital Therapeutics Autism Market Research Report 2033. _Growth Market Reports_. https://growthmarketreports.com/report/digital-therapeutics-autism-market
    
- Shah, S. M., Madhavan, S. P., Bowden, N., & Nedgungadi, P. (2026). Caregivers’ experiences with autism from pre- to postdiagnosis: Multi-country perspectives using ecological systems theory. _Research in Autism_, _132_, 202836. https://doi.org/10.1016/j.reia.2026.202836
    
- Sohn, J., Lee, E., Kim, J., Oh, H., & Kim, E. (2025). Implementation of generative AI for the assessment and treatment of autism spectrum disorders: a scoping review. _Frontiers in Psychiatry_, _16_, 1628216. https://doi.org/10.3389/fpsyt.2025.1628216
    
- Terol, A. K., Meadan, H., Gómez, L. R., & Magaña, S. (2024). Cultural adaptation of an intervention for caregivers of young autistic children: Community members’ perspectives. _Family Process_, _63_(2), 691–710. https://doi.org/10.1111/famp.12999
    
- Wang, L., Mujib, M. I., Williams, J., Demiris, G., & Huh-Yoo, J. (2021, July 28). _An evaluation of Generative Pre-Training Model-based Therapy chatbot for caregivers_. arXiv.org. https://arxiv.org/abs/2107.13115
    
- World Health Organization: WHO. (2025, September 17). _Autism_. https://www.who.int/news-room/fact-sheets/detail/autism-spectrum-disorders
    
- Yaacob, W. N. W., Yaacob, L. H., Muhamad, R., & Zulkifli, M. M. (2021). Behind the Scenes of Parents Nurturing a Child with Autism: A Qualitative Study in Malaysia. _International Journal of Environmental Research and Public Health_, _18_(16), 8532. https://doi.org/10.3390/ijerph18168532