# Parse Tree — resume_01.resume

Ejemplo válido — perfil completo, con 2 experiencias y 2 qualifications. 

mermaid
classDiagram
    class Resume

    class PersonalInfo {
        name: Camila Restrepo
        location: Medellín, Colombia
    }

    class Contact {
        email: camila.restrepo@correo.com
        github: camilarestrepo
        phone: +57 300 555 1234
    }

    class Experience1["Experience 1"] {
        position: Backend Developer
        company: Rappi
        years: 3
    }

    class Experience2["Experience 2"] {
        position: Software Engineering Intern
        company: Bancolombia
        years: 1
    }

    class Education {
        institution: Universidad ICESI
        degree: B.Sc. in Systems Engineering
    }

    class Skill1["Skill"] {
        name: Java
    }

    class Skill2["Skill"] {
        name: Spring Boot
    }

    class Qualification1["Qualification 1"] {
        name: Backend Development
        level: Expert
    }

    class Qualification2["Qualification 2"] {
        name: Cloud Computing
        level: Intermediate
    }

    class Classification {
        label: Backend Developer
    }

    Resume --> PersonalInfo
    Resume --> Contact
    Resume --> Experience1
    Resume --> Experience2
    Resume --> Education
    Resume --> Skill1
    Resume --> Skill2
    Resume --> Qualification1
    Resume --> Qualification2
    Resume --> Classification
