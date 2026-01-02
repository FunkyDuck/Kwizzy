<script setup lang="ts">
import { ref } from 'vue'
import QuestionItem from '@/components/QuestionItem.vue'

defineProps({
  id: String,
})

const currentQuestion = ref(0)
const responses = ref<Array<boolean>>([])

const updateCounter = (resp: boolean): void => {
  currentQuestion.value++
  responses.value.push(resp)
}

const quizz = {
  name: 'Réseaux : Init',
  questions: [
    {
      question:
        "Une entreprise multinationale relie son siège de Paris à sa filiale de New York. De quel type de réseau s'agit-il ?",
      answer: 'WAN',
      choices: ['LAN', 'MAN', 'WAN'],
    },
    {
      question:
        'Dans votre salle de classe, tous les ordinateurs sont connectés à un commutateur central. Quelle est cette topologie ?',
      answer: 'Topologie en étoile',
      choices: ['Topologie en bus', 'Topologie en étoile', 'Topologie en train'],
    },
    {
      question: 'Citez le désavantage majeur de la topologie en Bus qui a conduit à son abandon.',
      answer: 'Tolérance aux pannes nulle',
      choices: [
        'Tolérance aux pannes nulle',
        'Coût de mise en place faible',
        'Nécessite un switch',
      ],
    },
    {
      question: 'De quelle couche est le câble RJ45 ?',
      answer: 'Couche 1 : Physique',
      choices: [
        'Couche 1 : Physique',
        'Couche 2 : Liaison',
        'Couche 3 : Réseau',
        'Couche 4 : Transport',
        'Couche 5 : Session',
        'Couche 6 : Présentation',
        'Couche 7 : Application',
      ],
    },
    {
      question: "De quelle couche est l'adresse IP (ex: 192.168.1.1) ?",
      answer: 'Couche 3 : Réseau',
      choices: [
        'Couche 1 : Physique',
        'Couche 2 : Liaison',
        'Couche 3 : Réseau',
        'Couche 4 : Transport',
        'Couche 5 : Session',
        'Couche 6 : Présentation',
        'Couche 7 : Application',
      ],
    },
    {
      question: 'De quelle couche est le protocole HTTP ?',
      answer: 'Couche 7 : Application',
      choices: [
        'Couche 1 : Physique',
        'Couche 2 : Liaison',
        'Couche 3 : Réseau',
        'Couche 4 : Transport',
        'Couche 5 : Session',
        'Couche 6 : Présentation',
        'Couche 7 : Application',
      ],
    },
    {
      question: "De quelle couche est l'adresse MAC ?",
      answer: 'Couche 2 : Liaison',
      choices: [
        'Couche 1 : Physique',
        'Couche 2 : Liaison',
        'Couche 3 : Réseau',
        'Couche 4 : Transport',
        'Couche 5 : Session',
        'Couche 6 : Présentation',
        'Couche 7 : Application',
      ],
    },
    {
      question: 'De quelle couche fait partie le routeur ?',
      answer: 'Couche 3 : Réseau',
      choices: [
        'Couche 1 : Physique',
        'Couche 2 : Liaison',
        'Couche 3 : Réseau',
        'Couche 4 : Transport',
        'Couche 5 : Session',
        'Couche 6 : Présentation',
        'Couche 7 : Application',
      ],
    },
    {
      question:
        "Remettez ces conteneurs dans l'ordre, du plus grand (celui qui contient tout) au plus petit : Segment, Trame, Paquet.",
      answer: 'Trame > Paquet > Segment',
      choices: [
        'Segment > Paquet > Trame',
        'Trame > Paquet > Segment',
        'Paquet > Segment > Trame',
        'Segment > Trame > Paquet',
      ],
    },
    {
      question:
        "Pourquoi un Switch (niveau 2) est-il plus rapide qu'un Routeur (niveau 3) pour traiter une donnée ?",
      answer:
        "Parce que le switch décapsule jusqu'à la couche 2, et le routeur jusqu'à la couche 3 ce qui demande plus de traitement processeur.",
      choices: [
        'Parce qu’un switch travaille en full-duplex alors qu’un routeur fonctionne en half-duplex.',
        'Parce qu’un switch utilise uniquement des adresses MAC, alors qu’un routeur doit convertir les adresses IP en adresses MAC avant de transmettre les données.',
        "Parce que le switch décapsule jusqu'à la couche 2, et le routeur jusqu'à la couche 3 ce qui demande plus de traitement processeur.",
        'Parce qu’un switch fonctionne exclusivement en matériel (ASIC), tandis qu’un routeur traite les paquets principalement via un logiciel.',
      ],
    },
    {
      question: "(Binaire vers décimal) : Convertissez l'octet 10101000.",
      answer: 168,
      choices: [],
    },
    {
      question: '(Décimal vers binaire) : Convertissez le masque 255.',
      answer: 11111111,
      choices: [],
    },
    {
      question: "(Hexadécimal vers binaire) : Convertissez l'octet d'adresse MAC F2.",
      answer: 11110010,
      choices: [],
    },
    {
      question:
        'Quel support utiliseriez-vous pour relier un PC de bureau à la prise murale située à 3 mètres ?',
      answer: 'Cuivre',
      choices: ['Cuivre', 'Fibre multimode', 'Fibre monomode', 'Wi-Fi'],
    },
    {
      question:
        'Quel support utiliseriez-vous pour relier deux bâtiments distants de 2 kilomètres ?',
      answer: 'Fibre monomode',
      choices: ['Cuivre', 'Fibre multimode', 'Fibre monomode', 'Wi-Fi'],
    },
    {
      question:
        'Quel support utiliseriez-vous pour connecter des tablettes pour des commerciaux qui se déplacent dans une salle de réunion ?',
      answer: 'Wi-Fi',
      choices: ['Cuivre', 'Fibre multimode', 'Fibre monomode', 'Wi-Fi'],
    },
    {
      question:
        'Quel support utiliseriez-vous pour relier un serveur à un switch dans une salle machine avec de fortes perturbations électromagnétiques (moteurs industriels à proximité) ?',
      answer: 'Fibre multimode',
      choices: ['Cuivre', 'Fibre multimode', 'Fibre monomode', 'Wi-Fi'],
    },
    {
      question:
        "Un administrateur réseau remplace tous les commutateurs (switchs) de l'entreprise par des modèles 10 Gb/s. Cependant, les câbles muraux sont vieux (Cat 5e).\n" +
        'Les utilisateurs pourront-ils bénéficier de la vitesse de 10 Gb/s ?',
      answer: false,
      choices: [],
    },
    {
      question:
        "Un administrateur réseau remplace tous les commutateurs (switchs) de l'entreprise par des modèles 10 Gb/s. Cependant, les câbles muraux sont vieux (Cat 5e).\n" +
        'Quelle sera la vitesse probable de la connexion (négociation automatique) ?',
      answer: '1Gb/s',
      choices: ['100Mb/s', '1Gb/s', '10Gb/s', '100Gb/s'],
    },
    {
      question:
        'Dans la norme T568B, quelles sont les deux couleurs positionnées sur les broches 1 et 2 (Transmission) ?',
      answer: 'Orange/Blanc-Orange',
      choices: ['Orange/Blanc-Orange', 'Vert/Blanc-Vert', 'Bleu/Blanc-Bleu', 'Brun/Blanc-Brun'],
    },
    {
      question:
        'Dans la norme T568B, quelles sont les deux couleurs positionnées sur les broches 3 et 6 (Réception) ?',
      answer: 'Vert/Blanc-Vert',
      choices: ['Orange/Blanc-Orange', 'Vert/Blanc-Vert', 'Bleu/Blanc-Bleu', 'Brun/Blanc-Brun'],
    },
    {
      question:
        'Le PC transmet sur les broches 1&2. Le Switch écoute sur les broches 1&2.\nQuel câble devez-vous utiliser ?',
      answer: 'Câble Droit',
      choices: ['Câble Droit', 'Câble Croisé'],
    },
    {
      question:
        'Le Switch est un équipement L2. Le Routeur est un équipement L3 (comme un PC).\nQuel câble utiliser ?',
      answer: 'Câble Droit',
      choices: ['Câble Droit', 'Câble Croisé'],
    },
    {
      question:
        'Si vous deviez relier directement le PC au port Ethernet du routeur (sans switch), quel câble faudrait-il ?',
      answer: 'Câble Croisé',
      choices: ['Câble Droit', 'Câble Croisé'],
    },
    {
      question: "L'adresse MAC suivante est-elle valide [00:11:22:33:44:55] ?",
      answer: true,
      choices: [],
    },
    {
      question: "L'adresse MAC suivante est-elle valide [00:GG:11:22:33:44] ?",
      answer: false,
      choices: [],
    },
    {
      question: "L'adresse MAC suivante est-elle valide [192.168.1.1] ?",
      answer: false,
      choices: [],
    },
    {
      question: "L'adresse MAC suivante est-elle valide [FF:FF:FF:FF:FF:FF] ?",
      answer: true,
      choices: [],
    },
    {
      question:
        'Si un ordinateur veut envoyer un message à tous les autres ordinateurs du LAN, quelle adresse MAC de destination doit-il écrire dans la trame ?',
      answer: 'FF:FF:FF:FF:FF:FF',
      choices: ['FF:FF:FF:FF:FF:FF', '192.168.1.1', '00:00:00:00:00:00'],
    },
    {
      question: 'Pourquoi y a-t-il une taille minimale pour les données (46 octets) ?',
      answer:
        'Pour avoir une longueur suffisante pour le mécanisme de détection de collisions (CSMA/CD).',
      choices: [
        'Pour ne pas être confondues avec les systèmes GSM.',
        'Pour garantir une transmission efficace et éviter une surcharge due à trop de petites trames sur le réseau.',
        'Pour avoir une longueur suffisante pour le mécanisme de détection de collisions (CSMA/CD).',
        'Pour assurer l’alignement mémoire des trames Ethernet dans les cartes réseau.',
      ],
    },
    {
      question:
        "Si une trame arrive avec un FCS incorrect au niveau d'un switch, que fait le switch ?",
      answer: 'Le switch détruit la trame car les données sont potentiellement altérées.',
      choices: [
        'Le switch met à jour sa table MAC mais ne transmet pas la trame.',
        'Le switch transmet quand même la trame mais ajoute un indicateur d’erreur afin que le destinataire puisse décider de la traiter ou non.',
        'Le switch renvoie une demande de retransmission à l’émetteur lorsque le FCS est incorrect.',
        'Le switch détruit la trame car les données sont potentiellement altérées.',
      ],
    },
    {
      question:
        'Imaginez un réseau composé de trois PC (A, B et C) reliés à un hub.\n' +
        'PC A veut envoyer des données à PC B.\n' +
        'PC C veut également envoyer des données à PC B.\n' +
        'A et C écoutent le câble, détectent le silence et commencent à transmettre exactement au même instant.\n\n' +
        'Que se passe-t-il ensuite selon la méthode CSMA/CD ?',
      answer:
        'Les signaux de A et C entrent en collision, A et C détectent la collision, arrêtent la transmission, envoient un signal de JAM, attendent un temps aléatoire puis retransmettent.',
      choices: [
        'Les signaux de A et C entrent en collision, A et C détectent la collision, arrêtent la transmission, envoient un signal de JAM, attendent un temps aléatoire puis retransmettent.',
        'Le hub détecte la collision et autorise l’un des deux PC à continuer la transmission.',
        'A et C terminent la transmission et PC B demande une retransmission après réception.',
        'A et C retransmettent immédiatement leurs données après la collision.',
      ],
    },
    {
      question:
        'Observez la topologie suivante :\n' +
        '2. Un Routeur est connecté à un Switch.\n' +
        '3. Le Switch est connecté à 3 PC et à un Hub.\n' +
        '4. Le Hub est connecté à 2 PC.\n' +
        'Combien y a-t-il de domaines de collision dans ce réseau ?',
      answer: 5,
      choices: [],
    },
    {
      question:
        'Observez la topologie suivante :\n' +
        '2. Un Routeur est connecté à un Switch.\n' +
        '3. Le Switch est connecté à 3 PC et à un Hub.\n' +
        '4. Le Hub est connecté à 2 PC.\n' +
        'Combien y a-t-il de domaines de diffusion ?',
      answer: 1,
      choices: [],
    },
    {
      question:
        'Imaginez un réseau composé d’un switch et de trois PC (PC1, PC2 et PC3).\n' +
        'Chaque PC possède une adresse IP différente (192.168.1.1, 192.168.1.2 et 192.168.1.3) et est relié à un port du switch.\n\n' +
        'Au départ, aucun PC n’a encore communiqué sur le réseau.\n' +
        'Ensuite, PC1 envoie des requêtes (ping) vers PC2 et PC3.\n\n' +
        'Le switch apprend alors les adresses MAC des machines et les associe à ses ports dans sa table MAC.\n\n' +
        'Question :\n' +
        'Si le switch reçoit une trame destinée à une adresse MAC qui n’est pas présente dans sa table, que fait-il ?',
      answer:
        'Il diffuse la trame sur tous ses ports sauf celui d’origine (flooding) jusqu’à identifier le bon destinataire.',
      choices: [
        'Il supprime la trame car l’adresse MAC est inconnue.',
        'Il diffuse la trame sur tous ses ports sauf celui d’origine (flooding) jusqu’à identifier le bon destinataire.',
        'Il envoie une requête ARP à tous les PC pour retrouver l’adresse MAC manquante.',
        'Il se met en mode hub de manière permanente pour toutes les communications suivantes.',
      ],
    },
  ],
}
</script>

<template>
  <section>
    <h1>Quizz : {{ quizz.name }}</h1>

    <div v-if="currentQuestion < quizz.questions.length && quizz.questions[currentQuestion]">
      <span>Question {{ currentQuestion + 1 }}/{{ quizz.questions.length }}</span>

      <QuestionItem
        :question="quizz.questions[currentQuestion]?.question"
        :answer="quizz.questions[currentQuestion]?.answer"
        :choices="quizz.questions[currentQuestion]?.choices || []"
        :userAnswer="null"
        @answered="updateCounter"
      />
    </div>

    <div v-else>
      <p class="has-background-info has-text-dark">
        Bravo, vous avez terminé le quizz.<br />
        Score: {{ responses.filter((r) => r === true).length }}/{{ responses.length }}
      </p>
    </div>
  </section>
</template>

<style scoped>
div {
  margin: 2dvh 0;
  p {
    margin: 2dvh 0;
    padding: 1dvh 1dvw;
    border-radius: 8px;
  }
}
</style>
