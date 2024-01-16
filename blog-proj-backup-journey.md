# Steering the Ship: Building a Robust PowerShell Backup Script with GenAI

[Back to Home](index.md)

> ***INFO*** - The below is a playful description of the building process.
> If you are more interested in the final code base, please follow [this link.](https://github.com/jcstrydom/robocopy-scripting)


<style>
    .first-image-container {
        float: left; /* Float the image container to the left */
        margin-right: 20px; /* Space between the image and the text */
        width: 40%; /* Adjust this as needed */
        max-width: 430px; /* Maximum width of the image */
    }

    .second-image-container {
        float: right; /* Float the image container to the left */
        margin-right: 20px; /* Space between the image and the text */
        width: 30%; /* Adjust this as needed */
        max-width: 430px; /* Maximum width of the image */
    }

    .image-container img {
        width: 100%; /* Make the image fill the container */
        height: auto; /* Maintain aspect ratio */
    }

    .text-container {
        overflow: hidden; /* Ensures the text wraps around the image */
    }

    @media (max-width: 600px) {
        .image-container {
            float: none;
            width: 80%; /* Larger percentage for smaller screens */
            margin: 0 auto 20px; /* Center the image and add space below on small screens */
        }
    }
</style>

<!-- <picture>
  <source media="(prefers-color-scheme: dark)" srcset="backup-images/DALL·E 2024-01-10 21.12.11-Boat_on_digital_rough_seas.png">
  <source media="(prefers-color-scheme: light)" srcset="backup-images/DALL·E 2024-01-10 21.12.11-Boat_on_digital_rough_seas.png">
  <img alt="Boat on digital rough seas" src="backup-images/DALL·E 2024-01-10 21.12.11-Boat_on_digital_rough_seas.png">
</picture> -->


<div class="content-container">
    <div class="first-image-container">
        <img src="backup-images/DALL·E 2024-01-10 21.12.11-Boat_on_digital_rough_seas.png" alt="Boat on digital rough seas">
    </div>
    <div class="text-container">
    </div>
</div>

**Good evening**, digital guardians and PowerShell enthusiasts!

In this blog, we take a closer look at the development of a PowerShell backup script, a project that blends traditional scripting with the innovative use of generative AI. This script, like a well-steered ship, represents a journey of technological evolution and practical knowledge-sharing.

### Initial Drafting: The AI-Assisted Beginning

Our journey began with generative AI laying the groundwork. The AI's first draft, while rudimentary, provided a foundational structure from which to build. This early version was like a sketch of a ship, outlining the basic shape but needing significant refinement and detail. An example of this refinement, was using of config files to insert parameters into the program without altering the code. These config files could take many formats, example `.txt`, `.json`, or `.yml`.

As a first iteration, I asked the LLM to add a `.txt` configuration file ...

### **Evolution from Text to YAML Configuration**

Recognizing the need for a more organized and robust approach, I transitioned from a `.txt` to a YAML file. This shift was like moving from a simple steering wheel to a full-fledged navigational console, providing more control and flexibility over the backup process. YAML's human interpretable format assists greatly with this.

### Crafting the YAML File: A Detailed Map

<div class="content-container">
    <div class="second-image-container">
        <img src="backup-images/DALL·E 2024-01-10 21.54.39-Map_with_route.png" alt="Map with plotted route over digital sea">
    </div>
    <div class="text-container">
    </div>
</div>

The YAML file, akin to a detailed map, now gave the ability to encompasses not just subdirectories but the entire backup strategy. It's the heart of the script's operation, guiding it precisely to what needs to be backed up and where it should be stored.

The strategy could now include:

* _Logfile Location_ -  the path to use where the logs will be saved to
* _Destination Directory_ -  the directory where the backup should be made to
* _Source Directories_ -  the directories to include in the backup

The script's default settings, particularly the Robocopy flags, are set. These settings are analogous to the sails of our ship, set to catch the wind efficiently, and can be adjusted or fine-tuned to suit different needs or to explore new efficiencies. Furthermore, these flags can also be included in the config file in future iterations.

 A benefit of using a config file, is multiple config files could enable different source directories which can be backup to varying destinations without changing any code. Rather just add or remove configs and run the script by passing in these config files. 

### **Running the Script: Navigating the Waters**

To run this script, one simply needs to prepare the YAML file and execute the `backup-script.ps1`. This process is comparable to setting the ship's course and then launching it, with PowerShell acting as the wind in its sails. The execution is straightforward, yet it's a crucial step in ensuring the safety of your data.

### **Troubleshooting: Navigating Challenges**

Every journey faces challenges, and running this script is no exception. If issues arise, the first step is to ensure the YAML file is correctly formatted and accessible. The log file serves as a record of the journey, offering insights into what might have gone wrong and how to correct it.

## **Closing Thoughts: The Value of Human Expertise**

This project highlights the dynamic interplay between AI-generated drafts and human expertise. While AI can create an initial framework, it's the nuanced understanding and experience of a software engineer or data scientist that brings the finer detail to life in the project. 

An example of this was while trying to improve the efficiency of the script, the ordering of using robocopy on the parent directory and then the subdirectories was sub optimal. By simply changing the order to first copy the subdirectories and the the parent directory which would use robocopy's '*already copied*' capability, created much efficiency gains in the running of the script.


***This demonstrates that, even in an age of advanced AI, the human element remains crucial in technology development.***

In conclusion, this PowerShell script is more than just a backup tool; it's a testament to the blend of AI assistance and human skill in software development. It underscores the importance of continuous learning and adaptation in the ever-evolving field of technology.

### Final Result

[Here](https://github.com/jcstrydom/robocopy-scripting) is the code that was created through this process.

**Until next time, may your data remain safe and your journey through the seas of technology be ever enlightening!**

<img align="left" src="backup-images\DALL·E 2024-01-10 21.14.42-Boat_on_digital_sea_towards_harbor.png" alt="Boat on digital sea towards harbor" />

[Back to home](index.md)