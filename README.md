# AI-RESUME-ANALYSER
AN AI-POWERED  APPLICATION THAT PARSES RESUMES, CALCULATES ATS SCORES, EXTRACTS CANDIDATE SKILLS, AND PROVIDES TAILORED JOB-MATCHING FEEDBACK.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         
import React, { useState } from "react";
import { AnalysisResult } from "../types";

interface ReviewComparisonProps {
  currentResult: AnalysisResult;


export const ReviewComparison: React.FC<ReviewComparisonProps> = ({ currentResult }) => {
  const [showOptimized, setShowOptimized] = useState<boolean>(true);

  return (
    <section className="bg-white border border-[#1A1A1A]/15 p-6 sm:p-8 mb-8 relative">
      {/* Editorial corner bracket accents */}
      <div className="absolute top-0 left-0 w-2.5 h-2.5 border-t border-l border-[#1A1A1A]/40" />
      <div className="absolute top-0 right-0 w-2.5 h-2.5 border-t border-r border-[#1A1A1A]/40" />
      <div className="absolute bottom-0 left-0 w-2.5 h-2.5 border-b border-l border-[#1A1A1A]/40" />
      <div className="absolute bottom-0 right-0 w-2.5 h-2.5 border-b border-r border-[#1A1A1A]/40" />

      <div className="flex flex-col gap-6">
        {/* Header and Toggle */}
        <div className="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 border-b border-[#1A1A1A]/10 pb-4">
          <div>
            <span className="text-[9px] uppercase tracking-widest text-[#1A1A1A]/50 block font-mono mb-1">
              Interactive Workspace / Edition 01
            </span>
            <h3 className="font-display text-2xl italic font-medium flex items-center gap-2 text-[#1A1A1A]">
              Review Comparison
            </h3>
          </div>

          {/* Styled Editorial Double Toggle Switch */}
          <div className="relative w-full sm:w-56 h-10 bg-[#E8E6E1]/30 border border-[#1A1A1A]/10 p-1 flex items-center">
            <div
              className={`absolute top-1 bottom-1 w-[46%] bg-[#1A1A1A] transition-all duration-300 ease-out ${
                showOptimized ? "left-[51%]" : "left-1"
              }`}
            />
            <button
              onClick={() => setShowOptimized(false)}
              className={`relative z-10 w-1/2 text-center font-mono text-[10.5px] font-medium uppercase tracking-[0.15em] transition-colors duration-200 ${
                !showOptimized ? "text-[#FDFCFB]" : "text-[#1A1A1A]/60 hover:text-[#1A1A1A]"
              }`}
            >
              Original
            </button>
            <button
              onClick={() => setShowOptimized(true)}
              className={`relative z-10 w-1/2 text-center font-mono text-[10.5px] font-medium uppercase tracking-[0.15em] transition-colors duration-200 ${
                showOptimized ? "text-[#FDFCFB]" : "text-[#1A1A1A]/60 hover:text-[#1A1A1A]"
              }`}
            >
              Enhanced
            </button>
          </div>
        </div>

        {/* Dynamic Display Grid */}
        <div className="bg-[#F4F2EE]/40 border border-[#1A1A1A]/10 p-6 min-h-[220px] relative overflow-hidden transition-all duration-300">
          {!showOptimized ? (
            <div className="animate-fade-in-up">
              <div className="flex items-center gap-3 mb-4 flex-wrap">
                <p className="font-display text-xl font-medium tracking-tight text-[#1A1A1A]">
                  {currentResult.targetRole}
                </p>
                <span className="text-[9px] font-mono font-medium tracking-widest uppercase bg-stone-200 text-stone-700 px-2.5 py-1">
                  Original Source
                </span>
              </div>
              
              <p className="mb-6 text-[#1A1A1A]/85 leading-relaxed font-light text-sm whitespace-pre-wrap">
                {currentResult.originalText || "No resume text submitted yet. Use the workspace below to begin analysis."}
              </p>

              {/* Critiques annotation feedback box */}
              {currentResult.originalText && (
                <div className="p-4 bg-white border border-red-200 border-l-4 border-red-600">
                  <p className="text-red-700 font-mono font-semibold text-[10px] mb-1.5 uppercase tracking-widest flex items-center gap-1">
                    <span className="material-symbols-outlined text-sm">warning</span>
                    ATS Flaw Critique
                  </p>
                  <p className="text-xs text-stone-700 font-normal leading-relaxed">
                    {currentResult.critiqueText}
                  </p>
                </div>
              )}
            </div>
          ) : (
            <div className="animate-fade-in-up">
              <div className="flex items-center gap-3 mb-4 flex-wrap">
                <p className="font-display text-xl italic font-semibold text-[#1A1A1A]">
                  {currentResult.optimizedRole}
                </p>
                <span className="text-[9px] font-mono font-medium tracking-widest uppercase bg-[#1A1A1A] text-[#FDFCFB] px-2.5 py-1 flex items-center gap-1">
                  <span className="material-symbols-outlined text-[12px] active-icon">auto_awesome</span>
                  AI Strategic Edit
                </span>
              </div>

              <p className="mb-6 text-[#1A1A1A] leading-relaxed text-sm md:text-base whitespace-pre-wrap font-normal">
                {currentResult.optimizedContent}
              </p>

              {/* Improvement annotation badge box */}
              <div className="p-4 bg-white border border-[#1A1A1A]/10 border-l-4 border-[#1A1A1A]">
                <p className="text-[#1A1A1A] font-mono font-semibold text-[10px] mb-1.5 uppercase tracking-widest flex items-center gap-1">
                  <span className="material-symbols-outlined text-sm active-icon">verified</span>
                  Verbal Architecture Advantage
                </p>
                <p className="text-xs text-stone-600 font-normal leading-relaxed">
                  {currentResult.improvementBadge}
                </p>
              </div>
            </div>
          )}
        </div>
      </div>
    </section>
  );
};
