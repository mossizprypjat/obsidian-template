Progress:
```dataviewjs
function renderProgressBar() {
    const container = dv.el("div", "", { attr: { style: `
            width: 100%;
            margin: 0 auto;
            padding: 1rem;
            display: flex;
            flex-direction: column;
            gap: 16px;
            align-items: center;
            justify-content: center;
            align: center; 
            background: rgba(255, 255, 255, 0.25);
            border-radius: 4px;
        ` 
    }});

	const progressText = dv.el("text")
	
    const progressBar = dv.el("progress", "", { attr : { max: "100", value: "0",
        style: `
            width: 95%;
        `
    }});

    container.appendChild(progressText);
    container.appendChild(progressBar);
    
    return { container, progressText, progressBar };
}


function calculateProgress() {
	const tasks = (dv.current()?.file?.lists || []).filter(({task}) => task);
    return Math.round([...tasks].reduce((acc, { checked }) => acc + 
	    Number(checked), 0) / tasks.length * 100 || 0);
}

function updateProgressBar({ container, progressText, progressBar }) {
		const progress = calculateProgress();
		if(typeof progress === 'number') {
		    progressBar.value = progress;
		    progressText.innerHTML = `${progress}%`;
		}
}
	
const progressBar = renderProgressBar();
updateProgressBar(progressBar);

setInterval(updateProgressBar, 500, progressBar);
```

- [x] **1 Done chapter**
  info about the chapter blabla, this chapter will not show up in `Tasks.md`.

|     | Gelezen | Geleerd | Oefeningen |
| --- | --- | --- | --- |
| keer | 1   | 0   | 0   |
| uur | 0   | 0   | 0   |

- [ ] **2 Todo Chapter**
  blablabla, this chapter will show up in `Tasks.md`.

|     | Gelezen | Geleerd | Oefeningen |
| --- | --- | --- | --- |
| keer | 1   | 0   | 0   |
| uur | 0   | 0   | 0   |