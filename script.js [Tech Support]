// Historical Data Object for Era Durations
const historicalEras = [
    {
        id: "slavery",
        name: "Legalized Slavery",
        years: "1619 – 1865",
        duration: 246,
        colorClass: "bg-red-500"
    },
    {
        id: "jim-crow",
        name: "Jim Crow & Legal Segregation",
        years: "1865 – 1965",
        duration: 100,
        colorClass: "bg-amber-500"
    },
    {
        id: "post-civil-rights",
        name: "Post-Civil Rights Era",
        years: "1965 – Present",
        duration: 61,
        colorClass: "bg-emerald-500"
    }
];

// Initialize and Render Visual Scale Dashboard
document.addEventListener("DOMContentLoaded", () => {
    renderEraBars();
});

function renderEraBars() {
    const dashboardContainer = document.getElementById("era-dashboard");
    if (!dashboardContainer) return;

    // Calculate total timeline window span dynamically
    const totalYears = historicalEras.reduce((sum, era) => sum + era.duration, 0);
    
    // Clear out hardcoded static placeholders
    dashboardContainer.innerHTML = "";

    // Generate responsive progress tracks dynamically
    historicalEras.forEach(era => {
        const percentage = ((era.duration / totalYears) * 100).toFixed(1);
        
        const eraRow = document.createElement("div");
        eraRow.className = "space-y-1";
        
        eraRow.innerHTML = `
            <div class="flex justify-between text-sm mb-1">
                <span class="font-semibold text-gray-200">${era.name} (${era.years})</span>
                <span class="text-gray-400 font-mono">${era.duration} Years (${percentage}%)</span>
            </div>
            <div class="w-full bg-gray-700 h-6 rounded-full overflow-hidden">
                <div class="${era.colorClass} h-full rounded-full transition-all duration-1000 ease-out" 
                     style="width: 0%" 
                     data-width="${percentage}%">
                </div>
            </div>
        `;
        
        dashboardContainer.appendChild(eraRow);
    });

    // Trigger visual loading animation smooth entry effect
    setTimeout(() => {
        const bars = dashboardContainer.querySelectorAll("[data-width]");
        bars.forEach(bar => {
            bar.style.width = bar.getAttribute("data-width");
        });
    }, 150);
}
