# TAP-Semantic-Consistency-Checking
This repository contains the supplementary material for the paper "Unleashing the Power of NLP Models for Semantic Consistency
Checking of Automation Rules" submitted to Journal of Visual Language and Computing.

The provided material includes the dataset used to train the classification models, as well as the source code necessary to replicate the experiments and generate the descriptions.

# Introduction
According to the IFTTT creation paradigm, when a user creates a new applet, the creator must specify a natural language description that summarizes how the applet works. By reading this field, a new user can more easily understand what an applet is for and decide whether or not to activate it on their device. However, on the part of IFTTT, there is no control over the content of the description entered by the user, so the creator could write anything, falsely describing the applet’s behavior. To this end, we built a new dataset to present all possible types of UDDs that a user can share on TAPs:
<ul>
  <li> <b> Completely Consistent UDDs: </b> These UDDs are coherent, aligning perfectly with both the trigger and action components. </li>
  <li> <b> Completely Inconsistent UDDs: </b> In contrast, these UDDs lack coherence with both the trigger and action components. </li>
  <li> <b> Partially Consistent UDDs: </b> This category includes UDDs that exhibit coherence with either the trigger component or the action component, but not both. </li>
</ul>

After this, we evaluated the samples of the dataset with three different NLP Classification Models that can check whether there is some semantic consistency between the trigger-action components of an applet and its natural language description provided by its creator. The classification models takes as input a pattern derived from the applet components and the corresponding user-defined description and outputs a similarity label.

# Creators
Bernardo Breve (bbreve@unisa.it), Gaetano Cimino (gcimino@unisa.it), Vincenzo Deufemia (deufemia@unisa.it), Annunziata Elefante (anelefante@unisa.it)

University of Salerno


# Dataset Information
In our study, we utilized the dataset proposed by Mi et al. [1] (<a href="https://www-users.cse.umn.edu/~fengqian/ifttt_measurement/">download</a>), which consists of a collection of IFTTT applets obtained from crawling the IFTTT.com site. This dataset includes crucial information such as a title (<i>Title</i>), a description explaining the applet behavior (<i>Desc</i>), the event triggering the applet (<i>TriggerTitle</i>) defined through a specific channel (<i>TriggerActionChannel</i>), the action to be performed (<i>ActionTitle</i>) selected from the corresponding channel (<i>ActionChannelTitle</i>), and the name of the applet creator (<i>Creator Name</i>).

We first defined a new pattern for <i>synthesizing</i> User-defined descriptions (UDDs) by carefully combining applet components, ensuring a coherent and accurate representation. Then, we conducted <i>dataset labeling</i>, a crucial process that involved assigning appropriate labels to the synthesized dataset, which enabled efficient categorization, organization, and analysis of the data. In particular, the pattern utilized for generating the synthesized UDD is as follows:

```
IF TriggerTitle (TriggerChannelTitle) THEN ActionTitle (ActionChannelTitle)
```

This standardized structure serves as a concise and comprehensive means of depicting the essential components and events associated with a specific applet. Then, the UDD-pattern pairs were labeled according to the following similarity label values:

<ul>
  <li> <b> ee: </b> This class denotes complete consistency between the UDD and the synthesized pattern, indicating that both the trigger and action components are accurately represented in the UDD. </li>
  <li> <b> cc: </b> This class denotes complete inconsistency between the UDD and the synthesized pattern, indicating that neither the trigger nor the action components are correctly aligned in the UDD. </li>
  <li> <b> ec: </b> This class denotes partial consistency between the UDD and the synthesized pattern, with a focus on the trigger component. Specifically, the trigger component in the UDD is correct, but the action component does not align with the pattern. </li>
  <li> <b> ce: </b> This class denotes partial consistency between the UDD and the synthesized pattern, with a focus on the action component. Specifically, the action component in the UDD is correct, but the trigger component does not align with the pattern. </li>
</ul>


An annotated sample is shown below.

```
{
    "Pattern": "IF Any new SMS received (Android SMS) THEN Send me an email (Email)",
    "Description": "A mail will be sent to yourself when you receive a sms",
    "Label": "ee"
}
```

# Relevant Papers

[1] Mi, X., Qian, F., Zhang, Y., Wang, X., 2017. An empirical characterization of IFTTT: ecosystem, usage, and performance, in: Proceedings of the Internet Measurement Conference, ACM. pp. 398–404

[2] Breve, B., Cimino, G., Deufemia, V., Elefante, A., 2023. A BERT-based Model for Semantic Consistency Checking of Automation Rules.
