# Document-Creator
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Advanced Document Creator</title>
    <style>
        body { 
            font-family: Arial; 
            background: #eef2f3; 
            margin: 0; 
            padding: 0; 
        }
        header {
            background: #0066ff;
            color: white;
            padding: 15px;
            text-align: center;
            font-size: 24px;
        }
        .container {
            width: 90%;
            margin: auto;
            margin-top: 20px;
        }
        .box {
            background: white;
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 20px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        select,textarea,button {
            width: 100%;
            padding: 12px;
            margin-top: 10px;
            border-radius: 8px;
            border: 1px solid #ccc;
        }
        button {
            background: #0066ff;
            color: white;
            border: none;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
        }
        button:hover {
            opacity: 0.9;
        }
    </style>
</head>
<body>

<header>🔥 Advanced Document Creator | Resume • Application • Letter</header>

<div class="container">
    
    <div class="box">
        <h2>Select Document Type</h2>
        <select id="docType" onchange="loadTemplate()">
            <option value="">-- Select Document Type --</option>
            <option value="resume">Resume</option>
            <option value="application">Job Application</option>
            <option value="leave">Leave Letter</option>
            <option value="custom">Blank Document</option>
        </select>
    </div>

    <div class="box">
        <h2>Document Editor</h2>
        <textarea id="editor" placeholder="Your document will appear here..."></textarea>
        <button onclick="generatePDF()">Download PDF</button>
    </div>

</div>


<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<script>
function loadTemplate() {
    let type = document.getElementById("docType").value;
    let editor = document.getElementById("editor");

    if(type === "resume") {
        editor.value =
`NAME:
Address:
Phone:
Email:

CAREER OBJECTIVE:
To secure a responsible career opportunity...

EDUCATION:
• Class 10th -  
• Class 12th -  
• Graduation -

SKILLS:
• Communication
• MS Office
• Teamwork

EXPERIENCE:
• Fresher / Experienced details

DECLARATION:
I hereby declare that...`;
    }

    else if(type === "application") {
        editor.value =
`To,
The HR Manager,
[Company Name]

Subject: Application for the post of [Job Title]

Respected Sir/Madam,
I am writing to apply for the position of...

Thanking you,
Yours faithfully,
[Your Name]`;
    }

    else if(type === "leave") {
        editor.value =
`To,
The Principal/Manager,
[School/Office Name]

Subject: Leave Application

Respected Sir/Madam,
I request you to grant me leave for...

Thanking you,
Yours sincerely,
[Your Name]`;
    }

    else {
        editor.value = "";
    }
}

function generatePDF() {
    const { jsPDF } = window.jspdf;
    let text = document.getElementById("editor").value;

    const pdf = new jsPDF();
    let lines = pdf.splitTextToSize(text, 180);
    pdf.text(lines, 10, 10);
    pdf.save("document.pdf");
}
</script>

</body>
</html>
