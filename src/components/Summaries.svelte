<script>
    import { currentChapter, currentPage } from '../store.js';
    import { ScrollArea } from "$lib/components/ui/scroll-area/index.js";

    export let chapterSummaries = [
        {
            "chapter": 1,
            "summary": "Eragon, a 15-year-old farm boy, finds a mysterious blue stone in the Spine, a mountainous forest near his home in Carvahall. He hopes it will bring money to help his family through the winter."
        },
        {
            "chapter": 2,
            "summary": "Eragon returns home with the stone but is unable to sell it at the local butcher, Sloan, due to its unknown origin. Disappointed, he keeps the stone, unsure of its value or purpose."
        },
        {
            "chapter": 3,
            "summary": "Eragon overhears the village storyteller, Brom, telling stories about the legendary Dragon Riders, long extinct but once protectors of the land. The stories fascinate Eragon, though he has no idea how relevant they will soon become to his life."
        },
        {
            "chapter": 4,
            "summary": "One night, the blue stone unexpectedly cracks open, revealing a dragon hatchling. Eragon realizes the stone was an egg and now finds himself bonded to the dragon."
        },
        {
            "chapter": 5,
            "summary": "Eragon keeps the dragon hidden, watching it grow rapidly, and he names it Saphira. He discovers their bond gives him the ability to communicate telepathically with her."
        },
        {
            "chapter": 6,
            "summary": "Eragon visits Brom, asking more about dragons without revealing that he has one. Brom grows suspicious and warns Eragon about the dangerous implications of such knowledge."
        },
        {
            "chapter": 7,
            "summary": "Eragon learns to care for Saphira, but tension grows as hiding her becomes increasingly difficult. Brom tells him about the dangers of the Empire, ruled by the tyrant King Galbatorix, and the evil Shade Durza."
        },
        {
            "chapter": 8,
            "summary": "The Ra'zac, cruel agents of the Empire, arrive in Carvahall looking for the dragon egg. Fearing for their lives, Saphira flies Eragon into the Spine, but they return to find Eragon's home destroyed and his uncle Garrow gravely injured."
        },
        {
            "chapter": 9,
            "summary": "After Garrow's death, Eragon is consumed by grief and a desire for revenge against the Ra'zac. He leaves Carvahall with Brom, who offers to help him track the Ra'zac and trains him in swordsmanship and magic along the way."
        },
        {
            "chapter": 10,
            "summary": "Eragon and Brom begin their journey in pursuit of the Ra'zac, learning the dangers of the Empire and the true extent of their mission. Saphira, though still growing, becomes a vital companion during their travels."
        },
        {
            "chapter": 11,
            "summary": "Eragon and Brom encounter the Ra'zac, but they are unable to capture them. The Ra'zac flee, and Eragon and Brom continue their pursuit, with Brom beginning to teach Eragon about swordsmanship and magic."
        },
        {
            "chapter": 12,
            "summary": "During their journey, Eragon grows more skilled in magic and learns more about the ancient language. Brom continues to give cryptic advice, but Eragon becomes frustrated by how much Brom withholds from him."
        },
        {
            "chapter": 13,
            "summary": "Eragon starts having vivid dreams of a woman imprisoned in a cell, not knowing that this is Arya, the elf who sent the dragon egg away from the Shade. He becomes increasingly curious about these visions."
        },
        {
            "chapter": 14,
            "summary": "The Ra'zac ambush Brom and Eragon, poisoning them, but they are rescued by a mysterious man named Murtagh. In the ensuing battle, Brom is mortally wounded and reveals that he was once a Dragon Rider."
        },
        {
            "chapter": 15,
            "summary": "Brom dies, leaving Eragon devastated. Before dying, Brom confesses that he had once been bonded to a dragon named Saphira, who was killed by Galbatorix's forces."
        },
        {
            "chapter": 16,
            "summary": "With Brom gone, Eragon is left in Murtagh's care. They decide to continue pursuing the Ra'zac, while Eragon continues to practice magic on his own, using the knowledge Brom imparted to him."
        },
        {
            "chapter": 17,
            "summary": "Eragon, Murtagh, and Saphira face new dangers on the road, including a violent storm that tests their endurance. Eragon begins to bond with Murtagh, although he senses that Murtagh is hiding something."
        },
        {
            "chapter": 18,
            "summary": "The group arrives in the city of Teirm, where they meet Angela, a mysterious herbalist, and Solembum, a werecat. Angela gives Eragon a cryptic prophecy about his future, which leaves him anxious about what lies ahead."
        },
        {
            "chapter": 19,
            "summary": "Angela's prophecy weighs heavily on Eragon as they continue their journey. Murtagh remains secretive about his past, and Eragon starts to question his trustworthiness."
        },
        {
            "chapter": 20,
            "summary": "Eragon and Murtagh face off with enemies while continuing to search for the Ra'zac. Eragon's magic skills improve, but he feels increasingly uncertain about his role in the fight against the Empire."
        },
        {
            "chapter": 21,
            "summary": "As they near Gil'ead, Eragon has another vision of Arya, the imprisoned elf. Eragon becomes more determined to rescue her, believing that she is key to his destiny."
        },
        {
            "chapter": 22,
            "summary": "Eragon and Murtagh infiltrate Gil'ead and successfully rescue Arya from her prison. However, they are pursued by Durza, the Shade, who severely injures Eragon in the process."
        },
        {
            "chapter": 23,
            "summary": "Durza captures Eragon, who is thrown into a cell and tortured. Murtagh, Arya, and Saphira manage to rescue him, but the experience leaves Eragon shaken and haunted by his encounter with the Shade."
        },
        {
            "chapter": 24,
            "summary": "Arya reveals that she is an ambassador of the elves and has been working to protect the dragon eggs. She guides the group toward the hidden rebel group, the Varden, who are fighting against the Empire."
        },
        {
            "chapter": 25,
            "summary": "On the way to the Varden, Eragon and his companions are pursued relentlessly by the Empire's forces. Eragon's bond with Saphira deepens, and he grows stronger in both magic and combat."
        },
        {
            "chapter": 26,
            "summary": "The group reaches Tronjheim, the mountain city of the Varden. Eragon is introduced to Ajihad, the leader of the Varden, and is welcomed by the rebel group as a valuable ally."
        },
        {
            "chapter": 27,
            "summary": "Eragon meets the Council of Elders, who oversee the Varden's operations. He learns more about the Varden's war against the Empire and feels the weight of the expectations placed on him as a Dragon Rider."
        },
        {
            "chapter": 28,
            "summary": "Angela's prophecy begins to come true as Eragon finds himself increasingly involved in the Varden's plans. Tensions rise as the Varden prepare for a major battle against the forces of the Empire."
        },
        {
            "chapter": 29,
            "summary": "The Empire's forces, led by Durza, launch an attack on the Varden. Eragon joins the battle, fighting alongside the Varden to repel the invasion."
        },
        {
            "chapter": 30,
            "summary": "A massive battle ensues between the Varden and the Empire's forces. Eragon faces Durza in a climactic duel, and with the help of Saphira and Arya, he is able to kill the Shade, though not without great personal cost."
        },
        {
            "chapter": 31,
            "summary": "After the battle, Eragon is left with a deep scar and new responsibilities. He is hailed as a hero by the Varden, but he knows that his journey is far from over, with Galbatorix still a looming threat."
        },
        {
            "chapter": 32,
            "summary": "Eragon is given a Rider's sword, Zar'roc, which once belonged to Brom. He accepts his role as a Dragon Rider and begins to contemplate his next steps in the fight against the Empire."
        },
        {
            "chapter": 33,
            "summary": "Eragon reflects on his journey so far, realizing that his destiny is more complicated than he ever imagined. He resolves to seek out the elves in Du Weldenvarden to continue his training as a Rider."
        },
        {
            "chapter": 34,
            "summary": "As Eragon prepares to leave the Varden, he feels the weight of his responsibilities as a Rider and a leader in the fight against the Empire. With Saphira by his side, he sets out on the next chapter of his journey, knowing that greater challenges lie ahead."
        }
    ];
</script>

<style>
    .summary-item {
        margin-bottom: 15px;
    }
</style>

<div class="main">
    <h2>Chapter Summaries</h2>
    <p class="positionMarking">Current Chapter: {$currentChapter}, Current Page: {$currentPage}</p>

    <ScrollArea>
        {#each Array($currentChapter) as _, i}
            <div class="summary-item">
                <h4>Chapter {chapterSummaries[i].chapter}</h4>
                <p>{chapterSummaries[i].summary}</p>
            </div>
        {/each}
    </ScrollArea>
    
</div>
