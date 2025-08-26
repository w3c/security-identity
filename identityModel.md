# Identity Model

## Abstract
<!-- Identity in the context of national IDs -->
_Identity_ is a widely used term. It is often defined intuitively, based on the given context. For example, if we mention the term identity in the context of humans, we associate it with the existence of a given individual and a set of attributes or characteristics associated with the corresponding human being. The identity of a given person is often associated with its national identity that is defined as a set of attributes. These attributes are typically recorded at the time of identity issuance and bind a unique individual to an identifier. The binding of the identifier to the person is certified with a tamper-proof physical document, such as a passport or an identity card issued by a trusted authority.

Similarly, in the digital world identities play a crucial role. In some cases digital identities have a direct counterpart in the physical world, for example, a digital identity of a human being that is supposed to provide a digital representation of the corresponding physical identity. In other cases, for example, identities of machines or machines' components, it can become much harder to use our intuitive understanding of identities. Even in cases, where a digital identity has a physical counterpart, our intuition may be misleading, since physical properties (e.g., forgery protection of a fingerprint) may not have a digital equivalent.

The goal of this article is to define a "general" notion of what we call an _identity system_. This general notion is supposed to include the essential components that are required to talk about *identities*. In that sense, we want to provide a general model that enables us to compare different notions of identities and their interrelation.

# Terms

In this paragraph, we introduce a set of terms that are often used in the context of identities. Depending on the reference, the terms may have slightly different, but typically similar meanings. The reason for the differences is not inconsistency, but the fact that different references focus on different aspects of identities and thus use slightly different meanings for the terms. For example, whereas [1](https://www.w3.org/TR/vc-data-model-2.0/) describes the technical format of what is called a *verifiable credential* and does not focus on a specific type of identity, [2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-4.2pd.pdf) focuses on digital identities of humans that are related to an individual's national identity and the requirements for an infrastructure to establish a trustworthy relation between two types of identities.

## Entities, Subjects, Users

The central element of interest of an identity system are the objects that are assigned to or are associated with an identity (what ever an identity is for now). Unfortunately, only when talking about the most central element of an identity system, there seems to be no consensus on the basic terms alone:
- [1](https://www.w3.org/TR/vc-data-model-2.0/), [2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-4.2pd.pdf), and [3](https://www.identityblog.com/stories/2005/05/13/TheLawsOfIdentity.pdf) use the term _subject_
- [4](https://www.iso.org/obp/ui/#iso:std:iso-iec:24760:-1:ed-2:v1:en) uses the terms _subject/principal_, and _entity_

[1](https://www.w3.org/TR/vc-data-model-2.0/) describes a subject as a "thing about which claims are made", [2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-4.2pd.pdf) as a "person, organisation, device, hardware, network, software, or service", and finally [3](https://www.identityblog.com/stories/2005/05/13/TheLawsOfIdentity.pdf) as a "person or thing represented or existing in the digital realm which is being described or dealt with".


In [4](https://www.iso.org/obp/ui/#iso:std:iso-iec:24760:-1:ed-2:v1:en) a *principal* or *subject*, is defined as "entity of which identity information is stored and managed [...]", with the term _entity_ defined as an "item relevant for the purpose of operation of a domain that has recognizably distinct existence". Furthermore, it is noted that "An entity can have a physical or logical embodiment".

## Attributes

The next term that plays an important role in the context of identity systems are _attributes_. Similar to the previous term (entity, subject, user) there are slightly different definitions of what an attribute is:

[2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-4.2pd.pdf) describes an attribute as "A quality or characteristic ascribed to someone or something. An identity attribute is an attribute about the identity of a subscriber." (Note that a *subscriber* is a subject that is registered in an identity system.)

The Oxford dictionary describes a subject in a philosophical sense, as the "substance or core of a thing as opposed to its attributes".

In [3](https://www.identityblog.com/stories/2005/05/13/TheLawsOfIdentity.pdf), Cameron defines "'attributes' as the things expressed in claims, and the subject is the central substance thereby described.".

[1](https://www.w3.org/TR/vc-data-model-2.0/) does not define or use the term "attribute". What probably comes closest to our intuitive notion of an attribute that is assigned to a subject, is the object (JSON terminology) in the `credentialSubject` value. Its type is further defined by the elements of a list representing the value of the `"type"` name-value pair in the body of a credential.

[4](https://www.iso.org/obp/ui/#iso:std:iso-iec:24760:-1:ed-2:v1:en) defines an "attribute" as a "characteristic or property of an entity" and provides "entity type", "address information", "telephone number", "MAC address", or "domain name" as examples of possible attributes.

## Identifiers

A third central element of identity systems are *identifiers*. Intuitively, we could consider an identifier as an abstract representation of the objects of interest. If globally unique, identifiers allow others to refer to the same object and to express statements about the same subject.

In [1](https://www.w3.org/TR/vc-data-model-2.0/) an optional `id` property is defined that expresses an identifier and associates it with a certain value (e.g., UUDI, HTTP URLs, DIDs), "others are expected to use when expressing statements about the specific thing identified by the identifier." At the same time, there is a warning "Developers are reminded that identifiers might be harmful when pseudonymity is required."

Cameron in [3](https://www.identityblog.com/stories/2005/05/13/TheLawsOfIdentity.pdf) introduces different types of identifiers: "A universal identity system must support both “omni-directional” identifiers for use by public entities and “unidirectional” identifiers for use by private entities, thus facilitating discovery while preventing unnecessary release of correlation handles."

In [2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-4.2pd.pdf) identifiers are defined as "A data object that is associated with a single, unique entity (e.g., individual, device, or session) within a given context and is never assigned to any other entity within that context."

[4](https://www.iso.org/obp/ui/#iso:std:iso-iec:24760:-1:ed-2:v1:en): defines an _identifier_ as an attribute or a set of attributes that uniquely characterizes an identity in a domain.

## Claims

To associate attributes with entities (subjects or users) claims are introduced. According to [1](https://www.w3.org/TR/vc-data-model-2.0/) "A claim is a statement about a subject." and furthermore "Claims are expressed using subject-property-value relationships."

[2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-4.2pd.pdf) and [4](https://www.iso.org/obp/ui/#iso:std:iso-iec:24760:-1:ed-2:v1:en) do not explicitly introduce claims. However, [2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-4.2pd.pdf) describes a *credential* (see below) as "An object or data structure that authoritatively binds an identity -- via an identifier -- and (optionally) additional attributes, to at least one authenticator possessed and controlled by a subscriber". [4](https://www.iso.org/obp/ui/#iso:std:iso-iec:24760:-1:ed-2:v1:en) mentions that a credential can be "an attribute for the principal, e.g. by recording the unique number of the token issued"



[3](https://www.identityblog.com/stories/2005/05/13/TheLawsOfIdentity.pdf) defines a claim as "...an assertion of the truth of something, typically one which is disputed or in doubt". As examples for claims the author mentions "...(a claim) may assert that a subject knows a given key..." or "A set of claims might convey personally identifying information - name, address, date of birth and citizenship, for example."

## Credentials

[5](https://www.w3.org/reports/identity-web-impact) introduces _credentials_ as "things we present to claim our identities, whether in the physical or digital world". The article further references the Cambridge Dictionary, where a (digital) credential is "a piece of information that is sent from one computer to another to check that a user is who they claim to be or to allow someone to see information" ([Cambridge-Dictionary-Identity](https://dictionary.cambridge.org/dictionary/english/credential)). The authors thus see two aspects of credentials: proving of claims, such as who we are, and gaining access to information.

[4](https://www.iso.org/obp/ui/#iso:std:iso-iec:24760:-1:ed-2:v1:en) define credentials as "the representation of an identity for the use of authentication". [4](https://www.iso.org/obp/ui/#iso:std:iso-iec:24760:-1:ed-2:v1:en) takes credentials in digital and physical form into account.

[2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-4.2pd.pdf) notes that "... other protocols and specifications often refer to attribute bundles as credentials...", but that they "... will use the term attribute bundle...". Furthermore, it defines a credential as "an object or data structure that authoritatively binds an identity - via an identifier - and (optionally) additional attributes, to at least one _authenticator_ possessed and controlled by a subscriber." Credentials are thus associated with authentication or Personal Identity Verification (PIV).

[1](https://www.w3.org/TR/vc-data-model-2.0/) defines a credential as a "set of one or more claims made by an issuer. The claims can be about different subjects."

## Summary

The following diagram is supposed to summarize the most important aspects the terms introduced so far, as well as their interrelations. An *identity* could thus be understood as a association of an identifier and a set of attributes to a given subject. This association of the subject with the set of attributes may be understood as claims about a the subject. Last but not least, credentials can be understood as proofs of these claims, i.e., credentials allow somebody to verify that an identity indeed associates a given attribute (or set of attributes) with a subject.

![Overview](./Figures/identity.drawio.png)

# Roles

If we consider an identity to consist of a subject, an identifier, a set of attributes, and a set of credentials, then an *identity system* involves entities that create identities, entities that hold/control identities, and entities that consume identities. These entities could be understood a roles in the creation, the processing, and the use of identities during the lifetime of a given identity. Depending on the use case of an identity system there might by differing security requirements for the elements and entities involved in the identity system. For example, in the case of a so-called "self-sovereign identity system" the holder of an identity might have created the identity on his own, whereas for the case of a national electronic identity, the identity must be created by a federal agency of the corresponding country.

For the purpose of universality, we try to be as general as possible in our definitions of the roles in an identity system.

## Issuer

Within a given identity system, the *issuer* denotes the entity that creates or issues credentials that associate an identifier and possibly attributes using claims with subjects. In that sense, issuers create or issue identities. Depending on the use case there may be different requirements for the issuer. For example, if we consider a use case where the attributes associated with a given subject include a qualification of the subject to perform a task, one probably expects the issuer to have verified a subject's expertise in performing the task.. Similarly, if the attributes include biometric data about the subject, one would expect the issuer to have checked that the claimed biometric data indeed match those of the subject.

In contrast to properties that demand correctness of the content of credentials, there might be use cases where subjects have expectations about the issuer. For example, one might expect that the issuer does not disclose attributes associated with a given subject without the consent of the subject.

Similarly, there may be requirements about the association of identifiers with subjects, such as the fact that any identifier is uniquely assigned to a single subject or, conversely, that an issuer only assigns one identifier to a given subject.

## Holder

The holder is described as the entity that controls a given identity. For example, if a credential associates a cryptographic key with a subject, the holder is supposed to control the key. Note that the holder not necessarily corresponds to the subject. For example, an infant may be issued an identity card and thus is the subject of the corresponding national identity, however, the holder of the identity may be a parent. Similarly, an identity my be assigned to a computer or a device more generally, the corresponding holder may then be its owner.

## Verifier

Finally, there will be entities who use, for example, credentials to authenticate a subject. A credential may, for example, associate a public key with a subject. Based on a cryptographic identification protocol the subject or holder of the corresponding identity may then prove to a verifier that he or she controls the corresponding private key without revealing it.

In cases where issuer and verifier are separate entities, this is where trust comes in. In the authentication example, the verifier needs to trust the issuer that he has associated the correct key with the correct subject or holder. Also the verifier possibly needs to trust the subject (or holder) that he has not shared his secret with anybody else. In federated identity systems this role is called "service provider" (sometimes also called "relying party") that trusts in a similar way the so-called identity provider (the issuer in a federated identity system) who manages identities and authenticates holders of identities.

## Wallet

The last element of an identity system we want to discuss here is the so-called *wallet*. A wallet provides a secure storage option for the holder of one or multiple idenities and allows the holder to store credentials and keys, such a private keys, which belong to public keys that are attributes associated with a subject through credentials. Besides providing secure storage options, wallets often provide additional security features, for example, given a verifier's request about the value of attributes of an identity and a corresponding credential stored in the wallet, the wallet may derive a so-called "verifiable presentations" that extracts the required information from the credentials and thereby makes sure that the holder does not disclose unnecessary information, which may result in privacy violations.

## Summary

An identity system, as we have informally defined it here, consist of a set of data elements that are provided in well-defined format and a set of roles that create, process, own, store, hold the data elements. The central term *subject* allows to bridge the gap between the digital world and the real or physical world, i.e., it allows to assign or associate data elements with physical objects, such as humans.

In the following diagram, we try to order the terms and roles we have defined so far. The diagram is by far not complete, but is supposed to provide an intuitive understanding of the components of what we call an identity system.

![Summary](./Figures/summary.png)

# References

[1](https://www.w3.org/TR/vc-data-model-2.0/): Verifiable Credentials Data Model v2.0, W3C Working Draft
[2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-4.2pd.pdf): "Digital Identity Guidelines", P.Grassi, M.Garcia, J.Fenton, NIST Special Publication 800-63-3, 2017
[3](https://www.identityblog.com/stories/2005/05/13/TheLawsOfIdentity.pdf): "The Laws of Identity", K.Cameron, Microsoft, 2005
[4](https://www.iso.org/obp/ui/#iso:std:iso-iec:24760:-1:ed-2:v1:en): "ISO/IEC 24760-1:2019(en) IT Security and Privacy — A framework for identity management — Part 1: Terminology and concepts"
[5](https://www.w3.org/reports/identity-web-impact): "Identity & the Web", W3C


