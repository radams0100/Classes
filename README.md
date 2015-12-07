# Classes

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace MRU
{
    class PsychicMutant : Mutant
    {
        public int IQ { get; set; }
        public int PowerUsageCount { get; set; }

        public override int DangerQuotient()
        {
            return Level * IQ * PowerUsageCount;
        }
    }
}

namespace MRU
{
    class PhysicalMutant : Mutant
    {
        public int IQ { get; set; }
        public int Strength { get; set; }

        public override int DangerQuotient()
        {
            return Level * IQ * Strength;
        }
    }
}

namespace MRU
{
    abstract class Mutant : IDisplayable
    {
        public string CodeName { get; set; }
        public int Level { get; set; }

        public abstract int DangerQuotient();

        public void DisplayInformation()
        {
            Console.WriteLine(CodeName + " - DQ:" + DangerQuotient().ToString());
        }
    }
}

namespace MRU
{
    public interface IDisplayable
    {
        void DisplayInformation();
    }
}

namespace MRU
{
    class ElementalMutant : Mutant
    {
        public int Region { get; set; }

        public override int DangerQuotient()
        {
            return Level * Region;
        }
    }
}

namespace MRU
{
    class Program
    {
        static void Main(string[] args)
        {
            List<Mutant> mutants = new List<Mutant>();

            PsychicMutant ps1 = new PsychicMutant();
            ps1.CodeName = "Mindbender";
            ps1.IQ = 100;
            ps1.Level = 3;
            ps1.PowerUsageCount = 2;
            mutants.Add(ps1);

            PsychicMutant ps2 = new PsychicMutant();
            ps2.CodeName = "Svenghali";
            ps2.IQ = 120;
            ps2.Level = 4;
            ps2.PowerUsageCount = 1;
            mutants.Add(ps2);

            PhysicalMutant ph1 = new PhysicalMutant();
            ph1.CodeName = "Strongman";
            ph1.IQ = 80;
            ph1.Level = 2;
            ph1.Strength = 30;
            mutants.Add(ph1);

            PhysicalMutant ph2 = new PhysicalMutant();
            ph2.CodeName = "Biggy";
            ph2.IQ = 80;
            ph2.Level = 3;
            ph2.Strength = 20;
            mutants.Add(ph2);

            ElementalMutant em1 = new ElementalMutant();
            em1.CodeName = "FireDude";
            em1.Level = 4;
            em1.Region = 7;
            mutants.Add(em1);

            ElementalMutant em2 = new ElementalMutant();
            em2.CodeName = "RainGirl";
            em2.Level = 5;
            em2.Region = 6;
            mutants.Add(em2);

            foreach (Mutant mutant in mutants)
            {
                mutant.DisplayInformation();
            }

            Console.ReadKey();
        }
    }
}
