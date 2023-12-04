# laba5-second-part-
repository in ІР-13 group in 2023 regarding the 5th programming lab

from enum import Enum

class Atom:
    class Type(Enum):
        ISOTYPE = 1
        RADIOACTIVE = 2
        ION = 3
        ANTIMATTER = 4
        STABLE = 5

    def __init__(self, name, atomic_mass_unit, neutrons_number, protons_number, electrons_number):
        self.name = name
        self.atomic_mass_unit = atomic_mass_unit
        self.neutrons_number = neutrons_number
        self.protons_number = protons_number
        self.electrons_number = electrons_number

    def is_neutral(self):
        return self.neutrons_number == self.electrons_number

    def __str__(self):
        return f"Atom: {self.name}, Mass: {self.atomic_mass_unit}, Neutrons: {self.neutrons_number}," \
               f" Protons: {self.protons_number}, Electrons: {self.electrons_number},"


class Molecule:
    def __init__(self, name):
        self.name = name
        self.atoms = []

    def add_atom(self, atom):
        self.atoms.append(atom)

    def sort_atoms_by_mass(self):
        self.atoms.sort(key=lambda atom: atom.atomic_mass_unit)

    def find_average_mass(self):
        if not self.atoms:
            return 0
        return sum(atom.atomic_mass_unit for atom in self.atoms) / len(self.atoms)

    def __str__(self):
        return f"Molecule: {self.name}, Atoms: {[str(atom) for atom in self.atoms]}"

def main():
    hydrogen = Atom("Hydrogen", 1.008, 0, 1, 1)
    oxygen = Atom("Oxygen", 15.999, 8, 8, 8)
    carbon = Atom("Carbon", 12.011, 6, 6, 6)

    water = Molecule("Water")
    water.add_atom(hydrogen)
    water.add_atom(oxygen)
    water.sort_atoms_by_mass()

    print(water)

    print("Average Atomic Mass in Water:", water.find_average_mass())
    print("Is Hydrogen Neutral?", hydrogen.is_neutral())

if __name__ == '__main__':
    main()
